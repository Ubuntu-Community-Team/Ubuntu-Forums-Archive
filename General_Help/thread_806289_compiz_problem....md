---
title: "compiz problem..."
date: 2008-05-24
forum: General Help
---

### Post by daraman2000 on 2008-05-24
One day I decided that I wanted the cubeaddon plugin, so i GITted and MAKEd the plugin, and then did the same thing with Compiz, except i used sudo make install. 

After restarting my system, compiz doesn't work...

starting it from terminal, it gives:
```
dara@MasterFire:~$ sudo compiz --replace
compiz (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
compiz (core) - Fatal: No manageable screens found on display :0.0
```

I tried uninstalling and reinstalling compiz, disabling all plugins, etc. but nothing seems to help...

Strangely though, Compiz works fine on all other accounts, though... 

My graphics card is an NVidia GeForce Go 7300

Further information will be posted at request.

Thanks in advance!

---

### Post by Forlong on 2008-05-25
Try this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by daraman2000 on 2008-06-08
I managed to fix  compiz by doing random stuff (like erasing and recompiling the entire thing over), but I ran Compiz-check anyways. 

This is what I got:
```
dara@MasterFire:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: No path to Compiz found. 

Would you like to know more? (Y/n) y

 In case you did not compile Compiz manually, this will result in Compiz
 failing to run. The problem is presumably a result of you installing the
 proprietary fglrx driver manually or by script, which changed a certain
 config file to get itself on the whitelist. 


```
What does it mean?

Replies appreciated, thanks in advanced

---

### Post by Forlong on 2008-06-08
>  In case you did not compile Compiz manually, this will result in Compiz failing to run.
That's the important info.
The question is: did you compile Compiz from source or not?

---

