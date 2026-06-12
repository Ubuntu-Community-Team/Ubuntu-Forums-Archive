---
title: "hdparm not working -- not permitted"
date: 2005-08-08
forum: General Help
---

### Post by Jessehk on 2005-08-08
Please advise:

```


root@jesse:~ # hdparm -d1 /dev/dvd

/dev/dvd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)


```

Fedora Core 4 played DVD's no problem ( **without** me having to tweak something. ).

Furthermore, Mplayer worked perfectly. For me, it just freezes.

---

### Post by batteryacid on 2005-08-08
try it with sudo... should work. I can't even do a hdparm -t (just finds the speed) without using sudo, so i'd imagine that's your problem.

gah nevermind, you're running as root...  :-#

---

### Post by Sam on 2005-08-08
Try this:

Open /etc/modules, then make sure that piix and ide-core modules are before everything else like this:
```
piix
ide-core

ide-cd
ide-disk
ide-generic
lp
mousedev
# Other modules.....
```
Maybe that helps.

---

### Post by Jessehk on 2005-08-08
[QUOTE=Sam]Try this:

Open /etc/modules, then make sure that piix and ide-core modules are before everything else like this:
```
piix
ide-core

ide-cd
ide-disk
ide-generic
lp
mousedev
# Other modules.....
```
Maybe that helps.[/QUOTE]
 contents of /etc/modules

> 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse



---

### Post by Sam on 2005-08-08
So try
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

piix
ide-core

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
```
If it doesn't work don't forget to remove the piix and ide-core lines.

---

### Post by Jessehk on 2005-08-08
[QUOTE=Sam]So try
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

piix
ide-core

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
```
If it doesn't work don't forget to remove the piix and ide-core lines.[/QUOTE]
 It worked perfectly. 

Thanks for the help :) 

(No more choppy DVD, hoorah!)

---

### Post by Jessehk on 2005-08-10
[QUOTE=Jessehk]It worked perfectly. 

Thanks for the help :) 

(No more choppy DVD, hoorah!)[/QUOTE]
 Okay, the problem is as follows.

Everytime I start the computer, I have to enter the command

> 

sudo hdparm -d1 /dev/dvd



When I tried editing hdpram.conf, on bootup, I got a message that /dev/dvd was not found. 

In a later message, it then said it was mounting the filesystems. 

I believe the problem is that hdparm.conf is trying to do something to a drive that hasn't been mounted yet. 

How can I solve this problem?

---

### Post by jeremy on 2005-08-10
Go into your /etc/rcS.d folder and change the startup order of hdparm by setting it to S29

sudo mv SXXhdparm S29hdparm

I did this, and it got rid of that message, but caused other problems (I can't remember exactly what), so I set i back to S07hdparm
, still get the message, but all works fine.

---

### Post by Rogue21121987 on 2005-08-18
[QUOTE=Sam]So try
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

piix
ide-core

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
```
If it doesn't work don't forget to remove the piix and ide-core lines.[/QUOTE]

I assume adding piix is for intel chipsets?  What about AMD?

---

### Post by jeremy on 2005-08-19
That is correct, look at this post: [http://ubuntuforums.org/showpost.php?p=93238&postcount=5](http://ubuntuforums.org/showpost.php?p=93238&postcount=5)

---

### Post by Rogue21121987 on 2005-08-20
Thanks

---

