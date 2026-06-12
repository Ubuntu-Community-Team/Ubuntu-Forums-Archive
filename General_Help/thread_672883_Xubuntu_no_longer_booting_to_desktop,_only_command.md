---
title: "Xubuntu no longer booting to desktop, only command line"
date: 2008-01-20
forum: General Help
---

### Post by monkeybrain on 2008-01-20
Hi guys,

My girlfriend's laptop was working fine with Xubuntu, when it suddenly decided to stop booting into the GUI desktop. It now shows the Xubuntu splash screen while starting up but then goes to the command line with a login prompt.

How can I get the desktop back?

I tried using this command:

sudo /etc/init.d/gdm start

but it said it failed.

---

### Post by lizzard on 2008-01-20
Try to reinstall the video-driver for your graphic card. I had a similar problem which occured after the last update and it fixed it.

---

### Post by banewman on 2008-01-20
From the prompt type
ls /etc/init.d
and look for the gdm entry - if you can't find it type
sudo apt-get install gdm.
if it is there then you may need to reconfigure your video driver - type
sudo dpkg-reconfigure xserver-xorg
then choose defaults except for the video driver - choose vesa for safety first - it's a failsafe driver
then type
startx - let us know how it goes pls :)

---

### Post by monkeybrain on 2008-01-21
I've tried the process you described banewman, but it failed after I typed 'startx'. It repeated the message: "xauth: error while loading shared libraries: libXdmcp.so.6: cannot open shared object file: No such file or directory"

I'll try it again now, perhaps I did something wrong, but I choose all the defaults except for the video driver and size of the display.

---

### Post by monkeybrain on 2008-01-21
Some more information:

When it boots into the command line there are some messages, the last of which ends with:

"kinit: No resume image, doing normal boot..."

---

