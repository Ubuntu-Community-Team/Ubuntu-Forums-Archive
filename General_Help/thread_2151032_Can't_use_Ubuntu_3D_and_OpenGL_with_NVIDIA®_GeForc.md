---
title: "Can't use Ubuntu 3D and OpenGL with NVIDIA® GeForce® GT 520MX,Optimus on Ubuntu 12.04"
date: 2013-06-03
forum: General Help
---

### Post by danbuz on 2013-06-03
I posted before about problems using Unity 3D mode and playing games because I could not set nvidia drivers correctly.

I fresh installed ubuntu 12.04 and I found out I use 2d mode, this could not let me use My Unity, OpenArena etc, and ofcourse Compiz Effects.

So After reading and reading I tried with updating Nvidia-current, after this I tried bumblebee, and nothing worked.
I pissed off, and installed synaptic manager. After this I removed :

```
Removed the following packages:
jockey-common
jockey-gtk
nvidia-common
nvidia-current
nvidia-current-updates
nvidia-settings
nvidia-settings-updates
ubuntu-desktop
xserver-xorg-video-all-lts-quantal
xserver-xorg-video-nouveau-lts-quantal


```

Rebooted the system and *Voilà. *Now I use 3D, OpenGL and Effects.
I posted this thread because I received PM questions from users with similar problems if I was able to find out the answer. 
I posted this solution in another thread here, but it **was removed from administrators** and I don't know why.

So ppl, the problem is that you have 2 video cards, one is the nvidia and the other is integrated Intel, and thats why the system is confused.


Besides that I have question. After removing the packages above, should I expect problems concerning stability in the future?

Thanks in advance!

---

### Post by danbuz on 2013-06-03
Any Suggestions community???

---

### Post by danbuz on 2013-06-04
Can someone give me suitable answer?

---

### Post by zeljkojagust on 2013-06-04
By doing what you did, you actually didn't do anything. One thing you said is correct, your computer has two GPUs, one is Nvidia and other is GPU component of your CPU. With that as a fact and that you're running Ubuntu Linux (this goes for all Linux distros), you have two options. First is simple, check your computer BIOS and if you have an option to disable CPU GPU component, do it, and install latest Nvidia drivers available for Linux on Nvidia site. If you don't have that option in bios, than you will have to use Bumblebee. There are lots of tutorials on the web, also Ubuntu official one, how you can install it, and than run applications with "optirun" prefix. You can even start complete desktop session if you put optirun prefix in front of the command that starts your desktop session. I know for a fact that works with KDE and XFCE. 

Now as your solution goes, what you did is actually "nothing". Don't get me wrong, but in your trying to make graphics work, you probably installed 6 types of Linux headers and kernels which of each pulled it's version of nvidia drivers and dkms installed kernel module of video driver for each version. When you removed what you removed, you probably triggered one combination that actually installed OK and now it's working. That's what I think happened. 

Also you were removed from admin on other thread because your solution doesn't make any sense and it would just confuse people.

---

