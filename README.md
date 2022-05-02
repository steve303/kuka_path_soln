# path_analysis_hw
I'm sitting next to a multi-ton, 6dof, Kuka robot arm. It's not doing what I want it to do.

The robot takes in a list of points and does its best to go to those points in order. The thing is, I just fed it a bunch of points and the robot didn't look right. For instance, there is a section of the path I sent to the robot that is a bunch of circles, and instead of tracing out circles, the robot just sat there unmoving... Something is definitely amiss. 

## The ask
Here's where you come in. I want to know why the robots didn't follow my instructions. Fortunately for us, I managed to save some logs during the run:
 - path.csv These are the points I told the robot to go to. Generally, a bunch of loops in the xy plane. 
 - tracker.csv This is where the robot went as measured by some optical trackers. 

Your task: generate insights. The more graphs and sick visualizations, the better. Generally, what parameters of the input points correlate with error? 

## A word of caution about those logs...
 - The tracker points are logged in the tracker frame of reference. You are going to want to transform those points into the frame of reference of the path. No idea what the transform is between tracker points and the coordinates of the path, but I do know that there is no shear (just rotation and translation).  
 - Remember how I said that the robots don't go where they are supposed to go? Well, that's not entirely true. I threw in some "registration points" at the beginning of the commanded path. You'll notice those as points where the robot is commanded to go-to and dwell-at some positions in space. You can assume that the robot accurately hits those points. This should help transform the tracker readings into the coordinates of the path. 
 - Both the t_trk and the t_pth columns are in the same units: 19-digit unix timestamp. There might be a bit of clock desynchrony, but you can assume that's too small to worry about for now. 
 - The data here is very raw and potentially insufficient for grand conclusions. Do your best, and document your assumptions. 

## Submission
In order to submit the assignment, do the following:

1. Navigate to GitHub's project import page: [https://github.com/new/import](https://github.com/new/import)

2. In the box titled "Your old repository's clone URL", paste the homework repository's link: [https://github.com/Machina-Labs/path_analysis_hw](https://github.com/Machina-Labs/path_analysis_hw)

3. In the box titled "Repository Name", add a name for your local homework (ex. `path_analysis_soln`)

4. Set privacy level to "Public", then click "Begin Import" button at bottom of the page.

5. Develop your homework solution in the cloned repository and push it to Github when you're done. Extra points for good Git hygiene.

6. Send us the link to your repository.


May your servo drives be warm, and your hydraulic fluid never leak.
