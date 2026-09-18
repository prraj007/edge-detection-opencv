# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** B.PRAVEEN RAJ  
- **Register No:**212225040315

---

## Output
ORIGINAL

```
import cv2
import matplotlib.pyplot as plt

image = cv2.imread('Screenshot (196).png')

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
plt.show()
```
<img width="648" height="403" alt="image" src="https://github.com/user-attachments/assets/fccbbc2f-2b0e-492d-8e80-acd34122b8eb" />


###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map

```
import cv2
import matplotlib.pyplot as plt

image = cv2.imread('Screenshot (196).png')
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=5)
sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=5)

sobel = cv2.magnitude(sobel_x, sobel_y)

plt.imshow(sobel, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
plt.show()
```
<img width="643" height="399" alt="image" src="https://github.com/user-attachments/assets/de4f7697-eaed-451d-92b6-18558c674bf9" />

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('Screenshot (196).png')
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

prewitt_x = np.array([[1, 0, -1],
                      [1, 0, -1],
                      [1, 0, -1]])

prewitt_y = np.array([[1, 1, 1],
                      [0, 0, 0],
                      [-1, -1, -1]])

x = cv2.filter2D(gray, cv2.CV_32F, prewitt_x)
y = cv2.filter2D(gray, cv2.CV_32F, prewitt_y)

prewitt = cv2.magnitude(x, y)

plt.imshow(prewitt, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')
plt.show()
```
<img width="645" height="400" alt="image" src="https://github.com/user-attachments/assets/1b2d3f0a-350a-43dc-8dfa-cee7a8647e1a" />

###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('Screenshot (196).png')
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

roberts_x = np.array([[1, 0],
                      [0, -1]])

roberts_y = np.array([[0, 1],
                      [-1, 0]])

x = cv2.filter2D(gray, cv2.CV_32F, roberts_x)
y = cv2.filter2D(gray, cv2.CV_32F, roberts_y)

roberts = cv2.magnitude(x, y)

plt.imshow(roberts, cmap='gray')
plt.title('Roberts Edge Detection')
plt.axis('off')
plt.show()
```
<img width="643" height="399" alt="image" src="https://github.com/user-attachments/assets/b6d97a52-bc73-4935-9166-3b172edf7051" />

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes

```
import cv2
import matplotlib.pyplot as plt
import numpy as np

image = cv2.imread('Screenshot (196).png')
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

laplacian = cv2.Laplacian(gray, cv2.CV_64F)

plt.imshow(np.absolute(laplacian), cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()

```
<img width="644" height="401" alt="image" src="https://github.com/user-attachments/assets/f95bf2d8-24a8-4b6b-b70f-b51a40e35d6b" />


###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  

```
import cv2
import matplotlib.pyplot as plt

image = cv2.imread('Screenshot (196).png')
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

canny_edges = cv2.Canny(gray, 50, 150)

plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
plt.show()
```
<img width="642" height="404" alt="image" src="https://github.com/user-attachments/assets/a016bc00-ba32-445f-9084-76346e3412f2" />

---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
