---
title: "Use ubuntu on two diff computers"
date: 2007-12-18
forum: General Help
---

### Post by guitarist809 on 2007-12-18
Hey,

I've installed Ubuntu 7.10 to a USB hard drive, which I was originally using on my own computer (installed nvidia drivers, etc...)

However, I am using it to restore a friends computer, which has an ATI card. Whenever it boots up I get an XServer configuration error. I tried restoring a xorg.conf file, but it didn't help.

His computer is a Dell.

What can I do (like reset all the drivers)?

---

### Post by forestpixie on 2007-12-18
try reconfiguring X, it'll need sudo I think if you don't boot in recovery mode

```
dpkg-reconfigure -phigh xserver-xorg
``` and you'll need to answer as best you can - if you have problems with getting the ati to go try vesa

but if you take the usb back to your pc it'll be the same problem there I guess and you'll have to do it again,

try perhaps to copy the original xorg and then when you get back to yours with it boot into recovery and move the backup back
 to copy
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia
```

to move
```
mv /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
```

hope that helps some

---

### Post by r-mo on 2007-12-18
EDIT:  Sorry, I've just re-read your post and realised this is pretty irrelevant to what you're doing.  I was thinking of moving the usb hard drive between the computers on a regular basis.  Anyway here's what I wrote for anyone else who may look at this thread. 
-----

could you create an xorg.conf.ati and xorg.conf.nvidia

then make a script that ran before X was invoked that was something like:
```

#!/bin/sh
vendor=`/usr/bin/lspci | /bin/grep "VGA" | /usr/bin/awk '{print $5}'`
if [ "$vendor" = "nVidia" ]; then
      cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
else
      cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
fi

```

*** No where near guaranteed to work, not tested even slightly ***

---

