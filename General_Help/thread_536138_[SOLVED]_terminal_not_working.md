---
title: "[SOLVED] terminal not working"
date: 2007-08-27
forum: General Help
---

### Post by bobo69 on 2007-08-27
Hi. I'm new to both linux and ubuntu, and I'm having trouble opening a working terminal window through the gui. i go applications- accessories-terminal, and a window opens up, but it's just a blank white window. no prompt or anything. i think it might have something to do with my video settings or the nvidia driver that i installed, but im not too sure. any help would be much appreciated. ive attached a screenshot of the terminal in case it helps. thanks

---

### Post by jamvegan on 2007-08-27
Does any other application exhibit this behavior?  It does seem like it could have to do with your display settings, but I would think that it would affect other things, as well, if that were so.

---

### Post by bobo69 on 2007-08-27
everything else seems to be working fine. the only thing i can see that might be odd is that there arent any minimize/resize/close icons attached to any application windows. but like a said i just switched over from windows, and i don't know if it's supposed to be like that or not

---

### Post by jamvegan on 2007-08-27
> there arent any minimize/resize/close icons attached to any application windows
Yes, there should be, in the upper right corner of each window.

---

### Post by jamvegan on 2007-08-27
By the way, what version of Ubuntu are you running?  Some of your desktop icons look like they did in older versions.  (Or did you just choose a different theme?)

---

### Post by bobo69 on 2007-08-27
nope dont got any. any ideas?

---

### Post by bobo69 on 2007-08-27
feisty 7.04

---

### Post by bobo69 on 2007-08-27
changed the theme to crux. but changing back doesnt change anything except the colour scheme

---

### Post by jamvegan on 2007-08-27
Okay, I think that I know what your problem is, but I'm not sure how to fix it.  You do not appear to have *any* window manager running.  In fact, I wonder what would happen if you tried typing after opening your terminal?  Your terminal may be starting up just fine, there's just no window manager border around it.

How did you install Ubuntu?  Did any errors occur during the install process?  Have you changed any configurations that you can recall?

---

### Post by bobo69 on 2007-08-27
umm ok. first off i installed off a cd that came with july's linux pro magazine. second, i have tried  typing into the terminal, but nothing seems to show up( i think that its working too, but i just can't see whats going on). the only things i've done since install is install the driver for my video card, and change the desktop theme. i think my problem might have started when i installed the nvidia driver, but i can't recall

---

### Post by jamvegan on 2007-08-27
I thought of something that should fix these issues.  Open Synaptic (System->Administration->Synaptic Package Manager).  Search for ubuntu-desktop.  If it is not installed (empty box next to it), click the box and select Mark for Installation.  If it is installed (green filled box), click the box and select Mark for Reinstallation.  Then click Apply.

The ubuntu-desktop package contains a list of all of the packages that make up a standard ubuntu desktop installation.  Installing it ensures that all of those other packages are installed.

---

### Post by bobo69 on 2007-08-27
had to go to work, but will try it when i get home tonight. thanx for all your help

---

### Post by bobo69 on 2007-08-27
hmm. well i figured it out. seems enabling desktop effects was a no-no. everything looks good now. thanks again

---

### Post by jamvegan on 2007-08-28
Aha!  Glad you got it sorted out. :)

---

