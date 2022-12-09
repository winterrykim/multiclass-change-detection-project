### [MAICON Computer Vision Competition](https://aiconnect.kr/competition/detail/214)
This team project's goal was to perform multiclass change detection on aerial satellite images. The model performs segmentation, identifying different types of changes including reconstruction, renewal, and demolition.

<p align="center">
  <img src="https://github.com/winterrykim/multiclass-change-detection-project/blob/main/sample_image.PNG"  width="300" />
</p>

### Libraries
The project was mainly implemented by using [change_detection.pytorch](https://github.com/likyoo/change_detection.pytorch)

### Different Methods Experimented
Our team experimented multiple methods to solve the problem.

1. Filtering insignificant images(excluding images without change) during data preprocessing for training
2. One hot encoding 
3. Various albumentations (cropping, gaussian blur etc.)
4. Using [shadow removal libraries](https://github.com/YalimD/image_shadow_remover/tree/master/shadow_remover)
5. Using different losses(Jaccard Loss, Dice Loss, Jaccard Loss + Dice Loss, Cross Entropy Loss etc.)
6. Using different LR Schedulers (CosineAnnealing LR, Step LR)
7. Increasing the batch size

In conclusion, 1, 2, 3, 5, and 6 seemed to give meaningful effect on the result of this project.
Filtering images allowed the model to be trained on meaningful datasets. One hot encoding increased the accuracy by allowing the model to decipher demolition and renewal.  Various albumentation prevented the model from being overtrained on particular set of images. Hybrid loss increased the accuracy by 0.1~0.5%. Batch size seems to be the most significant factor.

### Further Reading and Potential Improvements
- Our team could have improved the accuracy and implementation if we have used [SDACD](https://github.com/Perfect-You/SDACD)
It resolves the problem related to shadow and error created by time-varying land cover changes. The link for research paper is [here](https://arxiv.org/abs/2204.00154)

- [Automatic Mixed Precision](https://pytorch.org/docs/stable/notes/amp_examples.html) allows [GPU acceleration](https://developer.nvidia.com/automatic-mixed-precision), increasing the limit of available batch size for training.

### Team Members
[Yeonsang Shin](https://github.com/yxxshin) <br /> 
[Terry Kim](https://github.com/winterrykim) <br /> 
[Sungkook Jung](https://github.com/ssoup0224) <br />
[GyuSeong Lee](https://github.com/codehuv)
