
**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I used Gaussian Blur for image smoothing to get rid of some noise.

I used Canny's edge detection algorithm to detect all the edges in the image. I defined the Region of Interest in order to be able to detect lines in a smaller image region. I then used Hough Transform to detect all the lines in the image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calculating the slope of each lines.
It was observed the negative slope pertains to left line and positive slope to right line. By computing the mean and standard deviation of these lines, I filter out the lines that fall outside the standard deviation. This also helps to reduce some mis-classification. Using the equation of line I extrapolated all the qualified lines to the corresponding boundary edges on y-axis, thus enabling me to take the average of the x-cordinates (top and bottom) and drawing tow line; one representing the left lane and the other representing the right lane. 

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when roads have turns.

Another shortcoming could be visibility issues due to rains/snow.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to segment the lane detection region of interest, to be able to detect curves in the lanes.

Another potential improvement could be to use some feedback loop in the pipeline to be able to get lane lines detected in n-1 and n-2 frames in order to detect lanes in absense of strong lane markers/visibility.
