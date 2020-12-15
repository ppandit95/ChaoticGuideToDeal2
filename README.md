# About the Guide
This is a supporting guide to get hold of deal.II tutorials that Dr. Bangerth has uploaded to understand its data structure in a intuitive way by playing around each example program . Although deal.II community is quite helpful and will resolve the various issues that one will encounter during this journey but an exhaustive exercise to get a grasp over this library is still missing . With this guide I intend to fill up this gap so that a new user can start up to utilise this library for his research.
# About the Author
I am Pushkar and have completed my graduate study  in Mechanical Engineering wherein I got to know about this library and in unsuccessful effort to get grasp over this library over past few months I look foward to frameout this guide which I found to be missing . Moreover, I do belieave that a lot of information often distracts us more than guide us . 
# About the Problem at Hand
Let's start at square one, In an attempt to carve out a potential guide to deal.II library I would look for a unique application problem which can be debugged in small chuncks to get hold of all the aspects of this library . Additionally to approach this very issue in an organized way is to explore deal.II library along with a standard textbook on Scientific Computing as well as finite element methods to make a wholesome attempt in this endeavour. I am willing to approach this library with both the pathways that I described above and to add some texture to it I am willing to carry out scientific computing with Julia as well as deal.II which will eventually be a comparative attempt.As for first case, consider a problem to simulate thermal profile in an additively manufactured part using birth technique which simply means to mesh entire geometry and activate finite elements as the simulation progresses. As well as for the second case, a book on "Scientific Computing : An Introduction using Maple and MATLAB" will be used in order to explore concepts with julai as well as deal.II.
# Out to Explore !

Fromthe first part of first tutorial with first_grid, we can utilize the learning to create our triangulation of the final additively manufactured part which is essentially a rectangle for initial purposes.To attain this, we creat a function called create_coarse_mesh() as - 

template <int dim>
void HeatEquation<dim>::create_coarse_grid ()
{
// Creation of two points
Point<dim> p1;
Point<dim> p2;
// Affecting coordinates to p1 and p2
for (unsigned int n=0; n<dim ; n++)
{
p1[n] = 0;
p2[n] = edge_length;
}
p2[dim-1] = layerThickness*number_layer;
// Generate a parallelopiped (rectangle in 2D) having a [p1 p2] diagonal
GridGenerator::hyper_rectangle(triangulation, p1, p2);
}

From here,one can essentially notice that we are modifying step 26 in order to reach our goal.I here we need to define certain variables in the class definition and pass dummy values (for the sake of qualitative simulation) in the constructor of HeatEquation . These are variables - edge_length(1.0),layerThickness(0.05) and number_layer(200). We will further call this very function inside the refine_mesh() function in order to perform adaptive mesh refinement based on heat source.
