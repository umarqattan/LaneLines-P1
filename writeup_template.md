# **Finding Lane Lines on the Road** 


### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

#### 1. First, convert the images to grayscale using the grayscale function, then use a histogram equalization to increase the contrast levels.

#### 2. Next, use gaussian_blur to add blurring to an image and use canny_edge to help with edge detection.

#### 3. Given the edge detected images, apply the region_of_interest function to narrow the image to only the edge detected region. This masks out the rest of the image, leaving the user with the edge detected region of interest. 

#### 4. Afterward, the hough_lines function is called in order to detect lines in an image.

#### 5. Given the detected lines from the hough_lines function, the detect_lanes function is called to detect any lane markers in the image. The hough_lines function can identify line_segments in the image, thus allowing the detect_lanes function to draw both sets of lane markers (namely left and right).


### 2. Identify potential shortcomings with your current pipeline

#### One potential shortcoming with the current pipeline would be what would happen if there is a sharp curvature in the road. For some reason whenever the car in a video begins to make a slight turn on the highway, the video pauses, plays one frame, then stops entirely. Currently, the pipeline does well with relatively straight roads. Not only this, but there is also an issue with the shakiness of the lane detector. Every frame, there seems to be an issue with the lane detector disappearing for 10ms or less.

#### Another potential shortcoming would be what would happen when the video footage were taken at night time where the light on the lanes is not as intense. If this happened, it can be solved by simply increasing the contrast in a grayscaled blurred version of the video (for each grayscaled frame in the video) and masking the video to isolate non-zero pixels using the region_of_interest function. In other words, this has already been taken care of.

### 3. Suggest possible improvements to your pipeline

#### A potential speed improvement to the current pipeline would be to use a dynamic programming technique to store previous accepted detected. This technique may help avoid recalculating similarly detected lanes to the ones currently found. This can also help with avoiding the shakiness and disappearance of the drawn lane detected lines for 10ms every frame.

#### A potetnial accuracy improvement to the current pipeline would be to use a different grayscale filter to improve lane detection. In the tutorial prior to the Lane Lines Project 1, an intensity vs. frequency graph was used to help illustrate the sharp differences between colors in an image. The areas of greatest change were critical in determining the largest gradient in an image, which can help tremendously with edge detection. 

#### The current pipeline does the job of identifying and drawing detected lane lines faily well. However, in the near future, I will most certainly implemeent the abovementioned pipeline improvements.

