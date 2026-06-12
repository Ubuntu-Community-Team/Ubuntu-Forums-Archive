---
title: "Please help with USB flash card"
date: 2007-06-16
forum: General Help
---

### Post by pelikan on 2007-06-16
Hi. I'm setting up a new install of Kubuntu Feisty. My USB flash card shows up in devices (KInfoCenter, USB Devices), but it doesn't mount so I can't read off of it. 

I made a mount point : /media/camera

The card reader seems to be: /dev/sdb

Thanks.

---

### Post by bobplano on 2007-06-16
have you tried
```
sudo mount /dev/sdb /media/camera
```
if you want it to auto-mount everytime you boot up, then you need to edit your /etc/fstab

---

### Post by langi280179 on 2007-06-16
Are you in plugdev - group? (Check via kdesu kuser)

After having checked that, i would manually mount the device (look via 'dmesg' for the messages appearing after pluging in).  I.e. if it's sdb1 (It's alway with a number)

```
sudo mount -t vfat /dev/sdb1 /media/camera

```
Post dmesg-output, if it does not help.

---

### Post by pelikan on 2007-06-16
> **bobplano said:**
> have you tried
```
sudo mount /dev/sdb /media/camera
```


Thanks. I tried that and got an error saying:

"mount: you must specify the filesystem type"

---

### Post by pelikan on 2007-06-16
> **langi280179 said:**
> Are you in plugdev - group? (Check via kdesu kuser)

After having checked that, i would manually mount the device (look via 'dmesg' for the messages appearing after pluging in).  I.e. if it's sdb1 (It's alway with a number)

```
sudo mount -t vfat /dev/sdb1 /media/camera

```
Post dmesg-output, if it does not help.

Ding! That did it. Thank you!

---

### Post by pelikan on 2007-06-16
Can you please tell me how to make it mount automatically when I plug it in?

Edit: Solved. I changed the entry in Disks and File Systems to say "/dev/sdb1" instead of "/dev/sdb."

---

### Post by bobplano on 2007-06-16
you need to edit your fstab
```
gksudo gedit /etc/fstab
```
then add something like
/dev/sdb1    /media/camera     vfat     and whatever options you want like rw
sorry about the wrong command  i did forget somethings in it

---

### Post by pelikan on 2007-06-16
Thanks a lot ya'll. It works now :)

---

### Post by langi280179 on 2007-06-16
Actually the udev-event sould to this for you. So i would check, whether you are member of plugdev, haldemon and udev before messing up with automagically mounting. If this does not help i would add an entry like this in  /etc/fstab;

/dev/sdb1      /media/camera     vfat    0 0

I doubt, the medium will be mounted automatically, though. So you will need to manually mount it.

There are more ellegant ways to to this, but i never needed them, so i don't know.

---

