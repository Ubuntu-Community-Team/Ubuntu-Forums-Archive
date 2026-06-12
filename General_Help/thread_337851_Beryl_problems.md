---
title: "Beryl problems"
date: 2007-01-13
forum: General Help
---

### Post by FastZ on 2007-01-13
Hey guys, I know there are tons of threads on here that speak of beryl problems and fixes but I am experiencing one that I can't find a fix for.  

uname -a shows that I now run the 2.6.17-10-386 kernel.  Before, when I had beryl working properly, i was running the 2.6.17-10-generic kernel.  All was fine back then.  I dont know when the kernel was updated and/or why it was updated but it's updated and now Beryl doesnt work for me.  

Synaptic shows that nvidia-glx is installed (version 1.0.9746), all required beryl packages (for version 0.1.4) are installed, and emerald is installed.  Howerver, when I open a terminal session and type "beryl-manager" and hit enter, I get the following output.  

```

desktop@linux:~$ beryl-manager
desktop@linux:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```beryl-manager starts and the ruby icon shows up on my taskbar but when I try to load the beryl window manager, all the windows flicker like it's trying to load up with beryl but then it goes back to metacity.  I've tried uninstalling the nvidia driver and reinstalling it which usually, at least a handful of times so far, breaks the xserver which then gives me a headache because I have to fix that!  I'm getting fairly proficient at repairing a broken xserver though.  Good experience!

I am at a loss as to why this may be happening, so I came here to, hopefully, find some help from you guys.  Any ideas?  Remedies?  Thanks a lot for your help.

---

### Post by smartbei on 2007-01-13
I had a similar problem. For some reason, the 386 kernel installed itself so I had to remove it.
To remove:
Reboot computer and at grub choose the option with the generic kernel. Open synaptic and remove linux-restricted-modules-386, linux-image-386, linux-image-2.6.17-10-386. Or, you could just change the grub boot order so that the generic image is the default. Search the forums for that if you wish. This would leave the alternative kernel installed, though useless.

---

### Post by FastZ on 2007-01-13
I tried to boot using the -generic kernel but i got a broken xserver blue screen while doing so.  the -386 kernel seems to work just fine except I cant get beryl to run.  I'll try to boot using -generic and come back with what happens.


Edit: Ok, I guess I had done something to break the xserver before which gave me the blue screen when I had tried to boot using the -generic kernel image.  This time, it worked just fine.  I booted, used synaptic to remove the -386 kernel image and files associated with it (along with a few 2.6.15 series kernel images that were still on here) but when I run the beryl-manager command in a terminal, I am still getting the Xlib errors as shown above.

Could it be something to do with the xorg configuration?  Or maybe something with the beryl install?  I really, really hate to remove and reinstall beryl due to have much of a pain it was to finally get it installed and running correctly before.  I'm open for any other suggestions anyone might have.  Thanks again.

Another thing I just thought of.  I read in a few other threads that concern beryl and the nvidia drivers and glx and whathaveyou and I saw mentioned something about the nvidia splash screen showing up or not showing up during boot.  I distinctly remember an nvidia splash screen showing up during boot before the gdm login screen shows up.  Now, that is not the case.  I see no nvidia screen during boot up.  Maybe this has to do with the nvidia driver?  As far as I know, it's the same driver I had used before when I initially installed beryl on my machine.

---

### Post by smartbei on 2007-01-15
hmmm...check the xorg.conf to see if it is using the nvidia driver. 

Are you noticing that 3d apps run slower?

BTW - the beryl install is usually pretty simple now - there are well built packages you can use. See:
[http://www.ubuntuforums.org/showthread.php?t=279456&highlight=beryl+svn](http://www.ubuntuforums.org/showthread.php?t=279456&highlight=beryl+svn) - for the latest and greatest (though slightly unstable at times) - currently at version 1.5
[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl+repository](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl+repository) - for version 1.4 - skip the whole part about installing your driver if youve done that already.

---

