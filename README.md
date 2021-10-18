# Model Predective Control - MPC in Motion
- Model predictive control (MPC) is an advanced method of process control that is used to control a process while satisfying a set of constraints. It has been in use in the process industries in chemical plants and oil refineries since the 1980s.
- For our assignment, we used the concept of model predictive control and applied it to a robot navigating in a scene, aiming to reach a certain end location or goal point from a given start point.

### Without Obstacle       With Obstacle
![without_obs](https://user-images.githubusercontent.com/44245211/137799458-26da3d51-ea3e-4aea-9422-230008a38193.gif)  ![with_obs](https://user-images.githubusercontent.com/44245211/137799455-8165fa84-70f4-41b7-9934-53f9e7c24587.gif)

# Outline of the Code
1. Create an empty image. This empty image represents our world. Now, we’ll add the start point, end (goal) point, and obstacles to it.
2. Mark the start and end points on it. This will be our world. The start point and end points are defined as a 2-tuple in the main code, and are marked in the image using red and green coloured (small) circles (having a radius of 5) respectively, by using the cv2.circle() function.
3. (If needed), add obstacles to the scene. By using in-built openCV functions like cv2.circle().
4. For the without obstacles case, all we have to do now, is to add the velocity constraints (i.e.
vmin < x_dot < vmax) and the robot equation i.e. x(n+1) = x(n) + x_dot * delta_t
5. Once all the constraints have been appended to the constraints array, the array is passed to
the cvxpy.solve() function, which is an in-built python optimization solver for convex
optimization problems.
6. For the with obstacles case, some additional effort needs to be put in, as we have to include
the obstacle avoidance constraints too. The obstacle avoidance constraints ensure that the robot does not choose a path which will collide with the obstacle.


# Directory Structure
- src folder contains the source code. The file names are self-explanatory
- results contains the outputs we got for both the cases. results_frames/With_obs_frames contains output for with obstacles case and results_frames/q2 contains outputs for without obstacles case
- misc is a miscellaneous folder
 
# Running the code
## Option-1: On Google Colab
1. Go to colab.research.google.com
2. Go to "src" folder. Upload the two files from your local PC to the colab repository
3. Load the file
4. Run the file

## Option-2: On local machine (Using Jupyter Notebook)
1. Install cvxpy from [here](https://www.cvxpy.org/install/). For linux machines, use the "build from source option" given in the website
2. Install other necessary libraries using: pip install requirements.txt. Alternatively, install matplotlib, opencv, and numpy manually.
3. go to "src" folder
4. Run the files using python

# To save the output
In both the files, uncomment the cv2.imwrite line. And change the directory path to your desired path.

##### Big Thanks to Pratikkumar Bulani!
