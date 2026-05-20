# AlexNet vs ResNet: A Comparative Study on CIFAR-10

## 📄 About This Research

This is a rigorous empirical comparison between two fundamental convolutional neural network paradigms:
- **Sequential Architecture** (AlexNet-variant)
- **Residual Learning Architecture** (ResNet-variant)

Both models were implemented from scratch using **PyTorch** and trained on the **CIFAR-10** benchmark dataset.

---

## 🎯 Key Findings

| Metric | AlexNet-variant | ResNet-variant |
|--------|---|---|
| **Final Accuracy** | 70.5% | 81.3% ✓ |
| **Training Loss** | 0.882 | 0.531 ✓ |
| **Trainable Parameters** | 35,855,178 | 207,946 ✓ |
| **Parameter Efficiency** | 1.97 acc/M | 391 acc/M ✓ |
| **Convergence Speed** | 45.7% (Epoch 1) | 55.3% (Epoch 1) ✓ |

### 🏆 Performance Gap
- **+10.8%** accuracy advantage (ResNet)
- **99.4%** reduction in model size
- **172x** fewer parameters with **superior** performance

---

## 📊 Experimental Setup

### Dataset
- **CIFAR-10**: 60,000 32×32 color images
- **Classes**: 10 categories
- **Split**: 50,000 training + 10,000 evaluation

### Hyperparameters
- **Optimizer**: Adam (α = 0.001)
- **Loss Function**: CrossEntropyLoss
- **Training Epochs**: 10
- **Normalization**: RGB mean/std = (0.5, 0.5, 0.5)
- **Hardware**: NVIDIA T4 GPU (Google Colab)

### Architecture Details

#### Sequential Model (AlexNet)
```
Conv2d → ReLU → MaxPool2d → ... → Flatten → FC → ReLU → Dropout → FC (Output)
Total Parameters: 35,855,178
```

#### Residual Model (ResNet)
```
Conv2d → ResidualBlock (F(x) + x) → ... → GlobalAveragePooling → FC (Output)
Total Parameters: 207,946
```

---

## 📈 Results & Analysis

### Convergence Speed
ResNet achieved **55.3% accuracy** in Epoch 1 vs AlexNet's **45.7%** — a **9.6 percentage point** lead from the start.

**Why?** Identity shortcut connections enable unimpeded gradient flow, accelerating weight updates across all layers.

### Final Performance
After 10 epochs:
- **ResNet**: 81.3% accuracy, loss = 0.531
- **AlexNet**: 70.5% accuracy, loss = 0.882

ResNet's steeper loss trajectory demonstrates convergence to a more favorable region of the loss landscape.

### Parameter Efficiency
The most striking result: ResNet's **207,946 parameters** outperformed AlexNet's **35,855,178 parameters**.

This validates the core ResNet insight: reformulating the learning objective as **residual mappings F(x)** (rather than unreferenced mappings H(x)) achieves substantially higher representational capacity per parameter.

---

## 🔬 Technical Insights

### Why ResNet Wins

1. **Vanishing Gradient Problem**: Identity shortcuts allow gradients to flow directly through deep networks without attenuation
2. **Efficient Representation**: Residual learning learns the *difference* from identity, requiring fewer parameters
3. **Global Average Pooling**: Replaces dense fully connected layers, dramatically reducing parameter bloat
4. **Early Convergence**: Superior gradient propagation leads to faster and better training dynamics

### Architectural Comparison

| Aspect | AlexNet | ResNet |
|--------|---------|--------|
| Gradient Flow | Sequential (potential bottleneck) | Direct shortcuts ✓ |
| Dense Layers | Large (heavy param count) | Minimal (GAP instead) ✓ |
| Depth Scalability | Limited (vanishing gradients) | Unlimited ✓ |
| Parameter Efficiency | Low (1.97 acc/M) | High (391 acc/M) ✓ |

---

## 💾 Files in This Research

- `AlexNet_vs_ResNet_FullPaper.pdf` - Full research paper with detailed methodology
- `AlexNet_vs_ResNet_LinkedIn.png` - Visualization of the paper (optimized for sharing)
- `README.md` - This file

---

## 🚀 Implementation

Both models were implemented from scratch in **PyTorch**:
- Custom layer initialization (Kaiming Uniform)
- Manual training loop with gradient computation
- Epoch-by-epoch performance tracking
- No data augmentation (to isolate architectural effects)

**Environment**: Google Colab with NVIDIA T4 GPU

---

## 🎓 Key Takeaway

**Under constrained computational budgets and limited training horizons, residual architectures offer a compelling combination of expressiveness and efficiency that classical sequential architectures cannot match.**

ResNet's identity shortcuts are not just an optimization—they fundamentally transform how deep networks learn.

---

## 📚 References

1. Krizhevsky, A., Sutskever, I., & Hinton, G. E. (2012). ImageNet classification with deep convolutional neural networks. *NeurIPS*, 25, 1097–1105.

2. He, K., Zhang, X., Ren, S., & Sun, J. (2016). Deep residual learning for image recognition. *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)*, 770–778.

3. Kingma, D. P., & Ba, J. (2015). Adam: A method for stochastic optimization. *International Conference on Learning Representations (ICLR)*.

4. Paszke, A., Gross, S., Massa, F., et al. (2019). PyTorch: An imperative style, high-performance deep learning library. *NeurIPS*, 32.

---

## 📝 Author

**Salva** — Independent AI Research  
*Aspiring AI Research Engineer | Computer Vision & Embodied AI*

---

## 🔗 How to Use This

1. **Share on LinkedIn**: Use `AlexNet_vs_ResNet_LinkedIn.png`
2. **Read Full Details**: Open `AlexNet_vs_ResNet_FullPaper.pdf`
3. **Quick Overview**: This README.md

---

*Preprint — Independent Research — 2026*
<img width="1080" height="1080" alt="7455802063419704325_avatar" src="https://github.com/user-attachments/assets/aef665c0-238d-4d3b-9b2e-355ce86cb817" />
