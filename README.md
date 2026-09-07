# WORKSHOP-3-DIP

# Workshop 3: Canny Edge Detection

## Overview
Canny Edge Detection is a multi-stage edge detection algorithm developed by John F. Canny in 1986. Widely regarded as the optimal detector in classical computer vision, it aims to satisfy three core criteria:
1. **Low error rate:** Detect real edges while minimizing false positives from noise.
2. **Localization:** Minimize the distance between detected edge pixels and true edge pixels.
3. **Single response:** Produce single-pixel-wide edges without duplicate responses for the same edge boundary.

---

## The 5-Stage Pipeline

* **1. Gaussian Smoothing:** Convolves the image with a Gaussian kernel to filter out high-frequency noise that causes false edge responses.
* **2. Intensity Gradient Calculation:** Uses Sobel kernels ($G_x$ and $G_y$) to compute the edge gradient magnitude and orientation ($\theta = \arctan(G_y / G_x)$).
* **3. Non-Maximum Suppression (NMS):** Thins the edges by checking neighboring pixels along the gradient direction, suppressing any pixel value that is not a local maximum.
* **4. Double Thresholding:** Classifies remaining pixels using two thresholds ($T_{low}$ and $T_{high}$):
  * **Strong edges:** Gradient $> T_{high}$
  * **Weak edges:** $T_{low} \le$ Gradient $\le T_{high}$
  * **Suppressed:** Gradient $< T_{low}$
* **5. Edge Tracking by Hysteresis:** Retains weak edge pixels only if they are directly connected to strong edges, suppressing isolated noise artifacts.

---

## Program --

**NAME:** SABEESHWARAN. P
**REG. NO:** 212225230234

```python
import cv2
import matplotlib.pyplot as plt

img = cv2.imread('myimage.png',cv2.IMREAD_GRAYSCALE)

blurred =cv2.GaussianBlur(img, (5,5),0)

edges = cv2.Canny(blurred, 50, 150)

plt.figure(figsize=(10,5))
plt.subplot(121),plt.imshow(img, cmap='gray')
plt.title('Original Image'), plt.axis('off')
plt.subplot(122),plt.imshow(edges, cmap='gray')
plt.title('Detected Edges'), plt.axis('off')
plt.show()
```

### OUTPUT - 

<img width="1038" height="390" alt="image" src="https://github.com/user-attachments/assets/02a81c26-55fc-4063-9efe-229134e308dd" />



### RESULT - 
  thus , the canny edge detection has been completed successfully.
