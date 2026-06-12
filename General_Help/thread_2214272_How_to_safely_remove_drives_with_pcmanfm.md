---
title: "How to safely remove drives with pcmanfm?"
date: 2014-03-31
forum: General Help
---

### Post by peysun1 on 2014-03-31
Hi,

With nautilus, drives can be safely removed: just right click on the drive, and choose the option "Safely Remove Drive".

I couldn't however figure out how this can be done with pcmanfm, although it reads explicitly that pcmanfm can safely remove drives:
[https://help.ubuntu.com/community/Lubuntu/PCManFM](https://help.ubuntu.com/community/Lubuntu/PCManFM)

Any help is appreciated.

---

### Post by bapoumba on 2014-03-31
Do not you have the remove drive symbol when inserting, for ex, an usb thumb drive ?
Please have a look at PCManFM > Prefs > Volume Management.

---

### Post by peysun1 on 2014-03-31
Thanks for the reply bapoumba!

>>Do not you have the remove drive symbol when inserting, for ex, an usb thumb drive ?
No, I don't get the removable drive symbol in pcmanfm, but I do get it in nautilus.
In my pcmanfm, the removable drive appears under /media.

Attached  is my volume management settings. For some reason, it seems to be  different than yours. (I use Lubuntu, and pcmanfm is its default file  manager).

---

### Post by bapoumba on 2014-03-31
It gets mounted in /media here too, that is normal. Can you right click and get an "Eject" option ?
What is you PCManFM version and the lubuntu release you are on ? (I'm on 14.04 so PCManFM is 1.2.0, that may explain the different menus you get).

---

### Post by peysun1 on 2014-03-31
No, I don't get ANY option (nautilus gives 8 different options, including Open, Open in New Tab, Open in New Window, etc).
I'm on 13.10 and my PCManFM is 1.1.2.
I didn't update my PCManFM since I don't know how to do that :(

---

### Post by bapoumba on 2014-03-31
My version is different because I  use a later ubuntu release. You cannot "upgrade" PCManFM without upgrading the whole distribution. Of course, there are ways to install a later application release on a previous ubuntu release, but I do not think that 1- it is necessary, 2- I'd like to be playing with that.

If you open /home/<your_user>/.config/pcmanfm/lubuntu/pcmanfm.conf, do you have these under the [volume] section ?
```
[volume]
mount_on_startup=1
mount_removable=1
autorun=1
```

If nautilus mounts and ejects the removable media fine, I suppose the system is doing what is required.

Would you happen to have another user on this computer ? Do you see the same issue ?

Edit : can you eject it by command line ?
```
sudo eject /media/<your_user>/<your_thum_drive_UUID>
```
You can find the thumb drive UUID with
```
sudo blkid
```
It is usually on /dev/sdb1 but that can vary.

---

### Post by vasa1 on 2014-03-31
> **peysun1 said:**
> Hi,

With nautilus, drives can be safely removed: just right click on the drive, and choose the option "Safely Remove Drive".

I couldn't however figure out how this can be done with pcmanfm, although it reads explicitly that pcmanfm can safely remove drives:
[https://help.ubuntu.com/community/Lubuntu/PCManFM](https://help.ubuntu.com/community/Lubuntu/PCManFM)

Any help is appreciated.

I have the same version of PCManFM as you do (1.1.2). My external drive is named "TOSHIBA EXT" and if I right-click on its icon in the side-panel, I see options to *mount* or to *unmount* it. IMO, unmount is the same (?) as eject safely provided you wait for a few seconds before yanking it out :)

BTW, Thunar 1.6.3 also just has the mount/unmount without the "eject safely". The image below is from PCManFM 1.1.2:

---

### Post by deadflowr on 2014-03-31
This should give you a good idea of what the differences between unmount, eject and safely remove mean in terms of Ubuntu
[http://askubuntu.com/questions/5845/what-is-the-difference-between-unmount-eject-safely-remove-drive-and-the](http://askubuntu.com/questions/5845/what-is-the-difference-between-unmount-eject-safely-remove-drive-and-the)

Maybe?

---

### Post by peysun1 on 2014-03-31
> **vasa1 said:**
> I have the same version of PCManFM as you do (1.1.2). My external drive is named "TOSHIBA EXT" and if I right-click on its icon in the side-panel, I see options to *mount* or to *unmount* it. IMO, unmount is the same (?) as eject safely provided you wait for a few seconds before yanking it out :) 

As I mentioned above (#5), the problem is that I don't get ANY option.

---

### Post by peysun1 on 2014-04-01
> **bapoumba said:**
> My version is different because I  use a later ubuntu release. You cannot "upgrade" PCManFM without upgrading the whole distribution. Of course, there are ways to install a later application release on a previous ubuntu release, but I do not think that 1- it is necessary, 2- I'd like to be playing with that.

If you open /home/<your_user>/.config/pcmanfm/lubuntu/pcmanfm.conf, do you have these under the [volume] section ?
```
[volume]
mount_on_startup=1
mount_removable=1
autorun=1
```


Yes I do.


> **bapoumba said:**
> 
Would you happen to have another user on this computer ? Do you see the same issue ?

Bingo! No, they don't see the same issue! Everything seems to work fine for them!

> **bapoumba said:**
> 
Edit : can you eject it by command line ?
```
sudo eject /media/<your_user>/<your_thum_drive_UUID>
```
You can find the thumb drive UUID with
```
sudo blkid
```
It is usually on /dev/sdb1 but that can vary.
Yes I can.

---

### Post by vasa1 on 2014-04-01
> **deadflowr said:**
> This should give you a good idea of what the differences between unmount, eject and safely remove mean in terms of Ubuntu
[http://askubuntu.com/questions/5845/what-is-the-difference-between-unmount-eject-safely-remove-drive-and-the](http://askubuntu.com/questions/5845/what-is-the-difference-between-unmount-eject-safely-remove-drive-and-the)

Maybe?
Great link. Thanks! [Maybe we should take this elsewhere]("http://ubuntuforums.org/showthread.php?t=2214389&p=12973843#post12973843") because it's an interesting topic by itself. Otherwise we could get infractions for derailing this thread ;)

---

### Post by bapoumba on 2014-04-01
> **peysun1 said:**
> Yes I do.
Bingo! No, they don't see the same issue! Everything seems to work fine for them!
Yes I can.
I'll have to search again, I found a link yesterday on how to reset PCManFM config files and start anew, dut I did not bookmark it. I'll edit this post or bump it with a new reply if I find it again. I think it was on the LXDE forums, but I'm not sure.
In case you find something useful in the meantime, before you remove said file (recommended workaround in said post), think about renaming first, so that you keep a backup copy. 


> **vasa1 said:**
> Great link. Thanks! [Maybe we should take this elsewhere]("http://ubuntuforums.org/showthread.php?t=2214389&p=12973843#post12973843") because it's an interesting topic by itself. Otherwise we could get infractions for derailing this thread ;)
Do you really think we would do that to you ? :tongue:
Thanks for starting a new thread.

---

