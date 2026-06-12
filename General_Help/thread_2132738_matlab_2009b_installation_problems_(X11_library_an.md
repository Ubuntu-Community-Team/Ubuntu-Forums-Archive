---
title: "matlab 2009b installation problems (X11 library and home folder problems)"
date: 2013-04-05
forum: General Help
---

### Post by ricardoojm on 2013-04-05
Dear all
I am trying to install matlab 2009b on my ubuntu 12.04 system, but some problems appeared.

First, at the end of the installation, there is a window saying that "the x11 library does not exist", and so matlab cannot work.

And when I open the matlab, there is an error message (in the command prompt) saying "the desktop configuration was not saved successfully".

I searched in some forums, and it seems that the solution for this second problem is because I am not defined as the owner of a file, and the solution may be something like:
 
[COLOR=#000000][FONT=verdana]sudo chown user: /home/user/.matlab/MATLABDesktop.xml[/FONT][/COLOR]

But the strange thing is that I dont have this folder in my system ([COLOR=#000000][FONT=verdana]/home/user/.matlab/[/FONT][/COLOR]), and neither the file [COLOR=#000000][FONT=verdana]MATLABDesktop.xml.
[/FONT][/COLOR]
It is weird, because first time I installed this version of matlab I didnt have these problems (it worked on a previous wubi install)

I would be very gratefull if someone can help me with that.
Best wishes

Ricardo


[COLOR=#000000][FONT=verdana][/FONT][/COLOR]

---

