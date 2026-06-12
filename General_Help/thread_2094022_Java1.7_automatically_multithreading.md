---
title: "Java1.7 automatically multithreading?"
date: 2012-12-12
forum: General Help
---

### Post by MutantJohn on 2012-12-12
Or is my scheduler just that good (in which case, suck it Intel!!! AMD >>>>>> Intel)? 

Okay, so for an intro to CS class I had to approximate pi by filling a unit circle with randomly generated points and calculating differences of areas, etc. I can attach the commented out source code if you guys really want. In fact, I should lol.

And coconuts = number of randomly generated points in unit circle. Oh, there was also a unit square, duh. But when I run this code for a large number of coconuts,1000000000 to be exact, I swear to God this code is multithreaded. 

How do I know this? Interesting question. I used 3 sources to test this, top, htop and Gnome's default system monitor and they all agree with each other.

The scheduler liked to have my code jump all across my processors so I bound it, using taskset -c 2,3 java CoconutPi, and even then they all agreed, I was using 197.1% CPU for this task, according to top, 2 independently running threads (PID is 3751 and 3752) of the same name each running at around 100% from htop and the system monitor agreed with top, as well.

So my question is, how is this possible? Or am I just hallucinating?

---

### Post by MutantJohn on 2012-12-12
//This was a particularly fun program that I enjoyed making.

import java.util.*;

//We name our class CoconutPi.

public class CoconutPi{


	public static void main(String[] args) {

//We define 4 doubles to be used as variables, obviously. x is
//intended to represent the position of a coconut in the 
//x-axis direction in a ranged from -1 to 1. y is, of course,
//the analog for the y-axis.
//r represents the radius of the unit circle we are assuming
//the coconuts are falling in.
//t is our estimated value of pi.

	double x,y,r,t;

//Here n and m are counters initialized to 0.

	double n = 0.0,m=0.0;
	
//We define a random number generator, named after the
//only woman my girlfriend need worry about me leaving
//her for. Granted, Mortred is fictional but nevertheless,
//I can but only dream and even dreams perturb us.

	Random mortred = new Random();

//We define a scanner and name it after one of Mortred's
//true counters given the proper weaponry, namely the
//Monkey King Bar.

	Scanner lanaya = new Scanner(System.in);

//We ask the user to give us a number of coconuts

	System.out.print("Please enter a number of coconuts (Integers, please. It's very hard to split coconuts on a desert island) : ");
	int coconuts = lanaya.nextInt();

//We begin our global timestep and for each timestep,
//we re-define x and y using our RNG, mortred.

	for (int i=0;i<coconuts;i++){

	x = 2*(mortred.nextDouble())-1;
	y = 2*(mortred.nextDouble())-1;

//The method inCircle is called to calculate the radius
//given Cartesian coordinates, x and y.
	
	r = inCircle(x,y);

//So, if r>1 then that means the coconut is outside
//the unit circle. n is our counter of this.

	if (r>1) {
	n=n+1;
	      }   

//If r<=1 then it is inside the unit circle. Here, m
//is our counter.
	
	if (r<=1) {
	m=m+1;
	   }
	}
		
//We calculate pi using the relation between the areas. For
//the unit circle, the area is pi*radius^2. For a square
//perfectly set around it, the area is (2*radius)^2.
//Thus the area of the circle divided by the square yields
//the relation pi/4. 
//We imitate this by using the number of coconuts inside the
//circle and square respectively, most mimicking the way
//a painting done by pointillism is.

	t=4*m/(n+m);
	
//We then print useful data out for the user.

	System.out.println((int)m+" of "+(int)(n+m)+" coconuts were inside the circle. And as such, we have estimated Pi to be : "+t);

	}

//Simple code used to calculate radius.

	static double inCircle(double a,double b) {
	
	   double c;
	 
	   c = Math.sqrt((a*a)+(b*b));
	   return c;
	   
	}


}

---

### Post by MutantJohn on 2012-12-12
Alright, so I looked at the processing tree using htop.

What's being created and then used? Java's generating 14 threads. There's one root thread and then 13 nested ones. These are all NLWP treads (ps -o nlwp <PID of my code> = 14) so Java's got 14 idle threads just sitting while it waits for the user to input a number of coconuts.

The instant I put in the max 10^n that Java can handle (or my processor or w/e), the main thread maxes out a core and then the bottom thread maxes out another. So the root tree goes like this, /sbin/init -> gnome-terminal -> bash -> java CoconutPi and then /sbin/init -> gnome-terminal -> bash -> java CoconutPi -> java CoconutPi. I can attach a screenshot too but it shouldn't be necessary.

Not only that but the S column of htop has the root thread with a status of S (sleeping) and the nested thread at R (running). htop tells me there's 2 processes running, also. So can a sleeping process actually eat up a CPU? Because htop really seems to think so.

---

### Post by MutantJohn on 2012-12-13
This a bump because I am genuinely curious.

Also, I'm afraid that while there are certain users here who would know the answer to my question, this is not the best place to ask. Is there a better forum I could go to with my specific question?

---

