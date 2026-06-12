---
title: "Gefore 8800 GS graphics refuse to work"
date: 2008-06-20
forum: General Help
---

### Post by macaholic on 2008-06-20
I just installed a Geforce 8800 GT in my Mac Pro today, and I'm already having issues. I nuked all references to my old card (ATI x1900xt) and reconfigured my xorg.conf before installing. On first startup I was put into safe graphics mode as I expected. First I tried installing the nvidia driver the manual way. it claimed to have succeeded, so I restarted. It did not work, so I uninstalled it and decided to give the driver in the repositories a try (the nvidia-glx-new package).Installation claimed to have succeeded once again, so I rebooted, and again, it did not work. I tried running the "NVIDIA X Server Settings" and it outputs this message "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." I have run that command several times and restarted X as well with no luck.
Additional information:
I am currently in safe graphics mode unable to change my resolution above 800x600, and my graphics card and monitor are undetected, leaving me with the vesa driver. My xorg.conf can be found [here]("http://ubuntu.pastebin.com/m5a577bdf"). Any help would be greatly appreciate, this is my first time dealing with nvidia drivers on linux, so please bear with me, however I coming from the world of ATI where configuring drivers is no easy task.
Also, I am an avid compiz-fusion user (compiel and run from the git) so any information you could offer about configuring an nvidia card to run with compiz support would be great as well.

---

### Post by sdennie on 2008-06-20
The nvidia drivers from the website install in a different way than the drivers from Ubuntu.  It sounds like you wanted to install the nvidia drivers from the website so, I recommend following the instructions from this post: [http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2](http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2) and then installing using the NVIDIA-whatever.sh installer.  Your xorg.conf looks correct to me so, that should work.

---

### Post by macaholic on 2008-06-20
Alright I entered that, but am currently having gcc issues when compiling the kernel module, will report back when I solve that.

---

### Post by sdennie on 2008-06-20
Is the problem you are having similar to this: [http://www.nvnews.net/vbulletin/showthread.php?t=114923](http://www.nvnews.net/vbulletin/showthread.php?t=114923)

If so, you might want to try 173.14.09 instead of the "latest" driver.

---

### Post by macaholic on 2008-06-20
Well thanks for your help, but I've decided after a ton of frustration with gcc and the nvidia driver, along with a bunch of other issues, I'm clean installing hardy. I am currently running the development branch (intrepid ibex) and I haven't clean installed since the development version of gutsy on this system, and it is really showing. I have other machines I am testing intrepid on, and since this is my main machine, I'm going to keep this one on the stable hardy for now. And now begins the download of the hardy ISO, it's going to be a long night.

---

### Post by sdennie on 2008-06-20
I see.  I didn't realize you were running Ibex.  That could certainly cause problems with the new kernel.

---

### Post by macaholic on 2008-06-20
Ya I was running 2.6.26, and the NVIDIA drivers have "preliminary support" for that kernel, whatever that means, however it refused to work on the other kernels due to a gcc problem. The issue being the older kernels were compiled with gcc 4.2, and the kernel will refuse all modules built with a different gcc than the kernel was built with, and Ibex does not have 4.2, so I attempted to manually install 4.2, which took FOREVER to compile, and it ended up doing nothing anyway.

---

### Post by macaholic on 2008-06-20
On another note, are there any good, preferably recent, guides to setting up a nvidia card with compiz fusion? If someone knows of some, I would love to see them.

---

