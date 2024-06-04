# Awesome-Multimodal-Large-Language-Models-With-Grounding
> A curated list of Multimodal Large Language Models (or Large Vision Language Model) with grounding ability. 


<!-- ## About Me: 
I'm an incoming Ph.D. student at the University of California San Diego. I recieved my M.S.E in Computer Science at Johns Hopkins University being a member of CCVL advised by [Alan Yuille](https://www.cs.jhu.edu/~ayuille/). I also work closely with [Haohan Wang](https://haohanwang.github.io/) from University of Illinois Urbana-Champaign.
Feel free to visit my [homepage](https://williamium3000.github.io/) and contact me for collaboration and discussion. -->


## Table of Contents
- [Awesome-Multimodal-Large-Language-Models-With-Grounding](#awesome-multimodal-large-language-models-with-grounding)
  - [Table of Contents](#table-of-contents)
  - [🔥 Large Vision-Language Model (ongoing)](#-large-vision-language-model-ongoing)
  - [🔥 Multi-modality (ongoing)](#-multi-modality-ongoing)

## 🔥 Large Vision-Language Model (ongoing)


<!-- template -->
<!-- <details>

  <summary>Paper name</summary>

  [Paper]() | [Github]() | [Project]()
  
   summary
  
</details> -->
<details>

  <summary>GPT4RoI: Instruction Tuning Large Language Model on Region-of-Interest</summary>

  [Paper](https://arxiv.org/pdf/2307.03601) | [Github](https://github.com/jshilong/GPT4RoI)

   1. propose referring for mllm by replacing placeholder <region_i> by feature obtained by mask pooling
  
</details>

<details>

  <summary>Osprey: Pixel Understanding with Visual Instruction Tuning</summary>

  [Paper](https://arxiv.org/pdf/2312.10032) | [Github](https://github.com/CircleRadon/Osprey)

   1. similar to GPT4RoI, Osprey also use mask representation to refer to entities in images. 
   2. It uses mask pooling to extract semantic features from image encoder and combines with a location extractor to process the mask and output spatial token.
  
</details>
<details>

  <summary>LISA: Reasoning Segmentation via Large Language Model</summary>

  [Paper](http://arxiv.org/abs/2308.00692) | [Github](https://github.com/dvlab-research/LISA)

   1. adapt LLM with mask decoder trained with segmentation datasets converted to LLM format ==> reasoning segmentation ability naturally emerges
   2. promote reason seg (complex reasoning requirement) benchmark
  
</details>

<details>

  <summary>VisionLLM: Large Language Model is also an Open-Ended Decoder for Vision-Centric Tasks</summary>

  [Paper](https://proceedings.neurips.cc/paper_files/paper/2023/file/c1f7b1ed763e9c75e4db74b49b76db5f-Paper-Conference.pdf) | [Github](https://github.com/OpenGVLab/VisionLLM)
  
1. unified interface for vision and vl tasks: points for detection, sample points for instance seg ==> instruction format for training
2. extra tokens & output-format-as-query to decode (faster)
  
</details>

<details>

  <summary>Unified-IO: A Unified Model for Vision, Language, and Multi-Modal Tasks</summary>

  [Paper](https://arxiv.org/abs/2206.08916) | [Github](https://github.com/allenai/unified-io-inference) | [Project](https://unified-io.allenai.org/)
  
   1. creates a unified IO for all sorts of vision and vl task (into discrete tokens)
   2. using t5-like encoder-decoder arch
  
</details>
   
<details>

  <summary>Unified-IO 2: Scaling Autoregressive Multimodal Models with Vision, Language, Audio, and Action</summary>

  [Paper](http://arxiv.org/abs/2312.17172) | [Github](https://github.com/allenai/unified-io-2) | [Project](https://unified-io-2.allenai.org/)
  
   1. following Unified-IO v1, creates a unified IO for all sorts of modalities including image, masks, bboxes, audios (into discrete tokens)
      1. dense masks are all binary, unlike v1 which specifies the color in text instruction (model struggles to follow)
   2. propose 2D Rotary Embedding, QK Normalization and Scaled Cosine Attention to stabilize training and scaling
   3. Mixture of Denoisers taining objectives
   4. instruction tuning of 220 tasks drawn from over 120 external datasets
</details>

<details>

  <summary>PixelLM: Pixel Reasoning with Large Multimodal Model</summary>

  [Paper](http://arxiv.org/abs/2312.02228) | [Github](https://github.com/MaverickRen/PixelLM) | [Project](https://pixellm.github.io/)
  
   1. learnable seg tokens + light-weight decoder
   2. a bunch of tricks:
      1. N x L seg tokens for L level multi-scale vision features. N tokens within each group for better modeling
      2. reweighted loss on regions with overlapping predictions
  
</details>

<details>

  <summary>PSALM: Pixelwise SegmentAtion with Large Multi-Modal Model</summary>

  [Paper](http://arxiv.org/abs/2403.14598) | [Github](https://github.com/zamling/PSALM)
  
   1. new paradigm: first generate mask proposal, then genereate mask and classification (following mask2former)
   2. instruction prompt + conditional prompt + candidate masks token
      1. three types of conditional prompt: classes, sentence (ref seg) and visual cues (point, scribbles, boxes, etc)
      2. conditional prompt => condition embed, candidate masks token => mask embed.
      3. condition embed +mask embed + image feature => mask2former decoder => bipartite matching loss + query-based decoding 
      ![图 0](images/398f94238fe61990ba3dd93ec6e1357359d45541ac7c22a06f0cb804f3bc2b4e.png)  
      
</details>

<details>

  <summary>LLM-Seg: Bridging Image Segmentation and Large Language Model Reasoning</summary>

  [Paper](http://arxiv.org/abs/2404.08767) | [Github](https://github.com/wangjunchi/LLMSeg)
  
   1. Use SAM to generate mask candidates, then fomulate the problem as mask selection (mask classification)
   2. promote LLM-Seg40K dataset, by using LLaVA to generate caption, then GPT4 to generate question-answer pair.
      
</details>

<details>

  <summary>GROUNDHOG: Grounding Large Language Models to Holistic Segmentation</summary>

  [Paper](http://arxiv.org/abs/2402.16846) | [Project](https://detgpt.github.io/)
   
   1. disantengle grounding with referring
   2. grounding as mask selection and train a mask2former+ to generate mask candidates
   3. referring by mask pooling on feature
   4. promote 2.5M M3G2 dataset
      
</details>

<details>

  <summary>DetGPT: Detect What You Need via Reasoning</summary>

  [Paper](http://arxiv.org/abs/2305.14167) | [Github](https://github.com/OptimalScale/DetGPT) | [Project](https://groundhog-mllm.github.io/)
   
   1. Follow LLaVA to tune VLM and for vqa
   2. Use grouding DINO to ground response generated by VLM to detect the relevantg entities.
      
</details>

<details>

  <summary>Ferret: Refer and Ground Anything Anywhere at Any Granularity</summary>

  [Paper](http://arxiv.org/abs/2310.07704) | [Github](https://github.com/apple/ml-ferret)
   
   1. propose hybrid region representation for referring : region name + coordinates + mask pooled feature by Spatial-aware visual sampler
   2. grounding through bbox
      
</details>

<details>

  <summary>Ferret-v2: An Improved Baseline for Referring and Grounding with Large Language Models</summary>

  [Paper](http://arxiv.org/abs/2404.07973)
   
   1. propose a bunch of improvements on Ferret v1
   2. including any-resolution (patches) for larger resolution
   3. DINOv2 Encoder for local feature extraction
   4. and High-resolution Dense Alignment stage between SFT and instruction turning.
  <summary>u-LLaVA: Unifying Multi-Modal Tasks via Large Language Model</summary>

  [Paper](http://arxiv.org/abs/2311.05348) | [Github](https://github.com/OPPOMKLab/u-LLaVA)
   
   1. propose to use different decoder for grounding (SAM for segmentation, Grounding DINO for detection)
      
</details>

<details>

  <summary>GSVA: Generalized Segmentation via Multimodal Large Language Models</summary>

  [Paper](http://arxiv.org/abs/2312.10103) | [Github](https://github.com/LeapLabTHU/GSVA)
   
   1. propose to Generalized Referring Expression Segmentation (GRES) in grounding LLM
      1. multiple object to ground
      2. need to reject null target
   2. propose to use multple [SEG] token to ground multiple objects (indicted by the texts before the [SEG] token), and [REJ] token to rej null target
      
</details>

## 🔥 Multi-modality (ongoing)

<details>

  <summary>GroundingGPT:Language Enhanced Multi-modal Grounding Model</summary>

  [Paper](http://arxiv.org/abs/2401.06071) | [Github](https://github.com/OPPOMKLab/u-LLaVA)
   
   1. grounding and referring of multi-modality in text
      1. bounding box by four relative coordinate values:[x1, y1, x2, y2]
      2. video timestamps by two two-digit decimals: {t1, t2}
   2. curate dataset for three stage training
      ![图 1](images/8f3a6cf2fec0f679487196ed6c48f94e076ae29ae311f8a888fcc8ce23e73e7c.png)  

</details>