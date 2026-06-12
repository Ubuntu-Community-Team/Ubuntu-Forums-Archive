---
title: "Dual Monitor Problems (span etc.)"
date: 2007-05-20
forum: General Help
---

### Post by enneth on 2007-05-20
I have been going through a lot of threads now, and I have not yet found an answer to my problem.
I am running Ubuntu Feisty with dual monitor on nVidia 7600 GT and the latest nVidia driver. I now have two options on how to use my two monitors. The first option is TwinView and second is to use "two separate x-screens".

If I enable two separate screens, Beryl crashes/does not work and I cannot launch the same application twice at the same time nor can I draw an application from one screen to another, so I figured it would be best if I tried to use TwinView. This fixed my problems with Beryl, I can now draw applications from screen to screen and  I can now run the same application twice at the same time.

But, of course, nothing is perfect. Now all my applications span over the two monitors when being launched or maximized, which I really hate, because there is a height difference between my two screens. Fx if I launch FireFox and visit ubuntuforums.org the text on the right screen is about 1 inch below the text on the left screen, causing serious reading distractions.

Therefore I would like to know if anyone has a solution to my problem, so all of my applications by default only open on one of the screens and not spans over both of them?

---

### Post by Rui Pais on 2007-05-22
> **enneth said:**
> ...

But, of course, nothing is perfect. Now all my applications span over the two monitors when being launched or maximized, which I really hate, because there is a height difference between my two screens. 
...

Hi,
try to add to your xorg.conf the following line:
> 	Option "NoTwinViewXineramaInfo"	"false"
on the same section where you have the Option "TwinView" and restart X server.

---

