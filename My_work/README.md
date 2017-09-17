# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./pipeline_steps/gray.jpg "Grayscale"
[image2]: ./pipeline_steps/edge.jpg "Edges"
[image3]: ./pipeline_steps/extraploted_solidWhiteCurve.jpg "Extrapolate"
[image4]: ./pipeline_steps/line_img.jpg "Lanes only"

---

### Reflection

### 1. Pipline description.
My pipeline contains 5 steps:
 #### 1.1) I converted the original image to grayscale
 ![alt text][image1]
 #### 1.2) Applied the guassian function for smoothing the gray scale image
 #### 1.3) Find out the edges from the image using canny method, and converted every other pixel to black
 ![alt text][image2]
 #### 1.4) Find out the region of the interest of the image
 #### 1.5) I have used the hough transformation function to find out the lines from the region(calculated above) of the image
 ![alt text][image4]

Once all the above steps are done then I have used weighted_img helper function to apply the output of the hough transformation function to original image to get the lines on the original image.

### 2. draw_lines()
In order to draw a single line on the left and right lanes, I modified the draw_lines():
#### 2.1) To find out the left and right lanes I have calculate the slope (m = (y2-y1)/ (x2-x1)). If m is less then 0 then it is left lane otherwise it is right lane.
#### 2.2) to extraplot the both left and right lanes, I have used the np.polyfit function to calculate the new m (slope) and b(constant) of the given x and y.
#### 2.3) Once calculate the new m and b. I got the min and max X points from both left and right lane
#### 2.4) Then using the new X points, I have claculated the new Y values using poly1d.
![alt text][image3]


### 3. Identify potential shortcomings with your current pipeline
It does not work if a car take left and right turn. Also, One shortcoming of my pipeline is not able to avoid the lines in the between the lanes. It happens when the color of the road changes in the video.

### 4. Suggest possible improvements to your pipeline
I feel the improvment can happen in hough transformation function to recognise the little curve in the line.