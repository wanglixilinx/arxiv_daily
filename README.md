# Tutorial for 4-bit FPN_ResNet18 for Semantic Segmentation on Cityscapes dataset

## Contents
1. [Installation](#installation)
2. [Usage](#Usage)

## Installation

* Install the torch, torchvision and some other requirements:

pip install torch torchvision tqdm Pillow scipy

## Usage

```
.{CURRET_PATH}
├── Dataset
│   ├── demo_images
│   └── cityscapes
├── encoding
│   ├── models
│   └── datasets
├── train_and_eval
│   ├── test.py
│   ├── demo.py
│   └── color_q4_results

```

### Support

#### low-bit Files

- [QFPN(ResNet18)] (encoding/models/fpnQ.py)

- [quantize files] (encoding/models/quantize.py & encoding/models/sim_bn_foldto_conv.py)

#### Weights for QFPN(ResNet18)

- [float] (encoding/weight/float.pth.tar)
- [4bit] (encoding/weight/q4/q6240.pth.tar)

### Demo 
```bash
cd train_and_eval 
sh run_demo_quantize.sh
```
### Evaluation on Cityscapes Validation
```bash
cd train_and_eval
sh run_eval_quantize.sh
```
|Input size | A/W bit | mIoU(val) | FLOPs |
|-----------|---------|-----|-------|
|256 * 512  | float | 62.9% | 10G |
| 256 * 512 | 4/4 | 62.0%  | 10G |

