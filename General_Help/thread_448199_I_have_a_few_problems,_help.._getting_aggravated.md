---
title: "I have a few problems, help.. getting aggravated"
date: 2007-05-18
forum: General Help
---

### Post by socialreject on 2007-05-18
First.. I've looked at forum threads tried them but I haven't been having any luck getting Ubuntu to support my monitors full native resolution of 1440x900. It will only go up to 1152x864.

And second, for some reason Azureus just stopped working. I just installed it earlier today and it was working fine until about 30 minutes or so ago when after I had to restart my computer after I was fiddling around with the stuff for the resolution. I tried to reopen it and it would act normal at first like it's starting up and it would open the torrents window but a second or so later, the window would just close and the program would quit.

If anyone could help me out with these two problems I would greatly appreciate it.

---

### Post by taurus on 2007-05-18
1.  What video card do you have and have you installed a driver for it?

2.  Try to run it from a terminal to see what the error message is.

```
azureus
```

---

### Post by socialreject on 2007-05-18
1. NVIDIA GeForce 6800. I installed the drivers from "Restricted Drivers Manager" and something from Synaptic I think too.
2. ```
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Fri May 18 20:47:41 GMT-05:00 2007  Data Missing /home/alex/Downloads/Azureus downloads/[DB]_Naruto_Shippuuden_014_[D10A7A23].avi
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb484d172, pid=6283, tid=3084757904
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid6283.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
```

---

### Post by taurus on 2007-05-18
You can edit /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```
and add that resolution, "1440x900", in there (at the beginning, before other resolutions) and see if you get that widescreen resolution after reboot.

---

### Post by socialreject on 2007-05-18
So do I add it in [here]("http://i2.photobucket.com/albums/y17/jmdaplaya/Hosted/Screenshot.png"). Where exactly? Heh, sorry, I'm a noob at Linux so I just don't want to mess anything up (well, more than I already have).

And as for Azureus after I first encountered it having problems I tried to uninstall it and reinstall hoping it would fix it but I had no luck.

---

### Post by socialreject on 2007-05-18
Also, I just saw that the refresh rate is set at 50 Hz and won't go any higher. It's odd because it seems like it was at 60 or 70 Hz earlier. I don't know if it's incorrect or what but that is way too low. I feel like it's having an effect on me though.

---

### Post by socialreject on 2007-05-18
bump.. please help

---

### Post by socialreject on 2007-05-19
Hmm, interesting... I tried messing around in the xorg file and I restarted and I can now use 1440x900 resolution. It lets me use a higher refresh rate than before (now 57 Hz) although I think It's still a bit too low but I've been told that it doesn't matter as much for LCD's, only for CRT's. I think Windows had the refresh rate running at 75 or 70 Hz though, so if I could get up it up there that would be nice. And I still need help with Azureus if anyone can help.

Thank you taurus for your help, I really do appreciate any help that I can get.

---

### Post by marty922 on 2007-05-20
> **socialreject said:**
>  And I still need help with Azureus if anyone can help.
.

I've had exactly the same trouble today.

Have a squiz at this thread

[http://ubuntuforums.org/showthread.php?t=447449&highlight=azureus]("http://ubuntuforums.org/showthread.php?t=447449&highlight=azureus")

or this one

[http://ubuntuforums.org/showthread.php?t=435935&highlight=azureus]("http://ubuntuforums.org/showthread.php?t=435935&highlight=azureus")

Some comments in the first thread worked for me.

Cheers,

Marty

---

### Post by RedSquirrel on 2007-05-20
This guide might help if you want to play around with refresh rates a bit more:

[URL="http://ubuntuforums.org/showthread.php?p=454217"]HOWTO: change resolution/refresh rate in Xorg - Ubuntu Forums
[/URL]

---

### Post by spedoinkle on 2007-07-27
```

rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*

```

:lolflag:

---

### Post by designwiz on 2007-07-27
Try this,

open terminal
sudo apt-get install nvidia-glx

after downloading this, then in the terminal type nvidia-settings a gui version will open where you can adjust the refresh rate/ resolution if all of them fail then try editing the xorg file!. Hope this helps!

p.s make sure u create a backup for the xorg file

---

