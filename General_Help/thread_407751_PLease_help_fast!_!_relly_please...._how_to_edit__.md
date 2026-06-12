---
title: "PLease help fast! ! relly please.... how to edit  xorg in recovery mode?"
date: 2007-04-12
forum: General Help
---

### Post by rigdzinthar on 2007-04-12
i was editing xorg.conf, to get dual head on this laptop here,
i saved back up on desk top, did not use proper command to back up
how do i edit xorg in recoery mode,
or what is the best way to fix this
x will not start...
thanks

---

### Post by srhlefty on 2007-04-12
If all you have is a console, then use an editor like vi or pico.  I personally haven't a clue how to use vi so I use pico.

---

### Post by Mithrilhall on 2007-04-12
As posted...if you have a working console just copy back the old xorg.conf file and you should be good to go.

---

### Post by rigdzinthar on 2007-04-12
i tried 
edit this edit taht... ya ya
but it said there is no display

---

### Post by bashologist on 2007-04-12
You should see something like this:
```
$ cd /etc/X11
$ ls
app-defaults             fonts    twm  xinit      xorg.conf.backup  xserver   Xsession.d        XvMCConfig
default-display-manager  rgb.txt  X    xorg.conf  Xresources        Xsession  Xsession.options  Xwrapper.config

$ sudo cp "xorg.conf.backup" "xorg.conf"
# Or if you don't have that file and you know how to edit your xorg:
$ sudo nano xorg.conf
```
What was the last thing you did before this problem? Were you trying to install a graphics driver? Or did you update anything?

---

### Post by jputman01 on 2007-04-12
Or if you have the ubuntu live disc still you can use that to edit xorg.conf.

boot the live disc 
mount your linux partition (mine is on sda3)
```
sudo mount /dev/sda3 /mnt
```
now your partition should be mounted
```
cd /mnt
```
check to see if you can see the files by using ls, if everthing is there then just edit the file
```
sudo gedit /mnt/etc/X11/xorg.conf
```

change whatever you need and save it.


acutally had to do this yesterday when i messed up my xorg.conf:o

---

### Post by rigdzinthar on 2007-04-12
i was just editing the xorg.conf
i did not do the back up command first before eidting
but i did save a copy of the original xorg.conf on the desktop
i am new on the command line,...
no new drivers... it was working fine

---

### Post by Mithrilhall on 2007-04-12
Then go to your desktop and issue a ...

cp xorg.conf /etc/...where ever it goes because I can't remember at the moment.

---

### Post by rigdzinthar on 2007-04-12
i am trying to use live cd, 
but i ont know how to mount properly,
i do not think mine is sd3,
i ooked in info it is ext3??
does htat help
please quic

---

### Post by jputman01 on 2007-04-12
> **rigdzinthar said:**
> i am trying to use live cd, 
but i ont know how to mount properly,
i do not think mine is sd3,
i ooked in info it is ext3??
does htat help
please quic

there is a command to list out your partitions i believe it is 
```
fdisk -l /dev/hda
```
or it may be /dev/sda depending on your type of hard disc, try them both, ill grab my laptop and see what command i used...

yes try the command above and it should list out your partitions look for the linux partition and the name will either hda# or sda#

then use 
sudo mount /dev/hda# /mnt
or
sudo mount /dev/sda# /mnt

whichever works for you besed on your HD

---

### Post by rigdzinthar on 2007-04-12
thanks for the help guys,
all done,
learning new things every day

---

### Post by jputman01 on 2007-04-12
did you get it to work using the live disc? or did you copy your saved file?

---

