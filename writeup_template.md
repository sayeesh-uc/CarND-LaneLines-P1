# **Finding Lane Lines on the Road** 

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on my work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

My pipeline consisted of: 
1. I converted the images to grayscale
1. Applied gaussian_blur to the grayed images, so that edge detection happens nicely.
1. Applied canny edge detection, as part of this, I experimented with various threshhold values to find the one that suites well.
1. Applied polygin masking to find the lanes in the area of intrest
1. Applied hough transformation to find the straight lines in the image. Tried various values to the threshold, min_length and max_gap values to find the ones that suite well. 
1. Filtered slopes that are too wide to rule out the noise.
1. As we have to draw 2 lines at the final solution, I used  Kmeans clustering on slope values to find 2 clusters.
1. Applied regression on the points in each cluster to find the average slope line to use.
1. Found the 2 points to draw the each line using the calucated regressed slope line.
1. Used weighted_add function to overlay the marker lanes on to the original image


### 2. Identify potential shortcomings with your current pipeline

1. Expects atleast one line is identified by hough transform on each side
2. Too much noise can cause the model to break
3. Curved lanes may not be detected well.
4. Blurred lanes, either white or yellow may not be detected well.


### 3. Suggest possible improvements to your pipeline
1. Apply filtering to highlight the white/yellow lanes.  i.e. increase contrast.
1. change from kmeans clustering to handcoded program to improve speed of the program.
1. Automatically detect and adjust the curves in the lane.