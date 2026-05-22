# UIE_cv
这是一个用来记录关于水下视觉增强的计算机视觉学习的仓库-基于论文WaveAlign: Wavelet-Domain Prior-Guided Color–Texture Alignment for Underwater Image Enhancement
#### 技术栈：Stable Diffusion Turbo (单步潜空间扩散模型) + LoRA 适配器 + 离散小波变换(DWT) + DCDD(低频色彩散度差异) + NDTSA(自然域纹理统计对齐)。

### 1.核心内容介绍
#### 1.1为什么用 DWT 而非 FFT？
水下退化是空间非均匀（近处轻、远处重；不同水质区域不同）退化，处理空间非均匀退化需要知道"退化发生在图像的哪个位置"，FFT将图像全局变换为频谱，空间维度被完全压缩
DWT能提供每个小波系数对应一个局部空间位置，频率+空间同时保留吗，NDTSA需要在空间局部区域做纹理统计对齐，DWT的分辨率保留是前提
#### 1.2DCDD模块的"可导性"——为什么用高斯软分配？
