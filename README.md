# SAM 2: Segment Anything Model - README

## Overview

Segment Anything Model 2 (SAM 2) is an advanced AI model designed to predict object masks in images and videos based on prompts. SAM 2 excels in interactive and automatic segmentation tasks, making it a powerful tool for various applications such as image editing, object detection, and video analysis.

## Features

### 1. Automatic Mask Generation

SAM 2 can automatically generate object masks over an entire image using the `SAM2AutomaticMaskGenerator` class. The process involves:
- **Grid Sampling:** Sampling single-point input prompts in a grid over the image.
- **Mask Prediction:** Generating multiple masks from each sampled point.
- **Quality Filtering:** Filtering and deduplicating masks using non-maximal suppression.
- **Advanced Options:** Enhancing mask quality by running predictions on multiple crops and postprocessing masks to remove small, disconnected regions and holes.

### 2. Prompt-Based Image Segmentation

The `SAM2ImagePredictor` class provides an easy-to-use interface for generating object masks from user-provided prompts. Key functionalities include:
- **Image Embedding:** The model converts an image into an embedding that enables efficient mask generation from prompts.
- **Flexible Prompting:** Supports various prompt types, including point prompts, box prompts, and masks from previous prediction iterations.
- **Efficient Prediction:** Once the image embeddings are set, the model can predict high-quality masks with minimal computational overhead.

### 3. Video Segmentation and Tracking

SAM 2 extends its capabilities to video segmentation with interactive features:
- **Frame-Level Interaction:** Users can add clicks or draw boxes on a video frame to generate and refine "masklets" (spatio-temporal masks).
- **Masklet Propagation:** Propagate clicks or boxes to generate masklets across the entire video sequence.
- **Multi-Object Tracking:** Simultaneously segment and track multiple objects across video frames.

## Usage Guide

### Automatic Mask Generation

To automatically generate masks for an image:

```python
from sam2 import SAM2AutomaticMaskGenerator

# Initialize the mask generator
mask_generator = SAM2AutomaticMaskGenerator()

# Generate masks for the image
masks = mask_generator.generate_masks(image)
```

### Image Segmentation with Prompts

To predict masks based on user-defined prompts:

```python
from sam2 import SAM2ImagePredictor

# Initialize the predictor and set the image
predictor = SAM2ImagePredictor()
predictor.set_image(image)

# Provide prompts and predict masks
masks = predictor.predict(prompts)
```

### Video Segmentation

For interactive video segmentation:

```python
from sam2 import SAM2VideoSegmenter

# Initialize the video segmenter
video_segmenter = SAM2VideoSegmenter()

# Add clicks or boxes on the frame to refine masklets
masklets = video_segmenter.add_clicks(frame, clicks)

# Propagate masklets across the video
video_segmenter.propagate_masklets()

# Segment and track multiple objects
video_segmenter.track_objects()
```

## Conclusion

SAM 2 is a versatile and efficient tool for object segmentation in images and videos. Whether you're working on image editing, object detection, or video analysis, SAM 2 provides state-of-the-art performance with its prompt-based and automatic mask generation capabilities.

For further information, consult the official documentation or explore the examples provided in the SAM 2 repository.
