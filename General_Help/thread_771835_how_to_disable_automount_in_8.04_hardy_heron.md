---
title: "how to disable automount in 8.04 hardy heron"
date: 2008-04-28
forum: General Help
---

### Post by gaebriel on 2008-04-28
Greetings all, I'm having a bugger of a time installing UT2004 and I believe it is due to automount issues. I have the DVD version and after entering the CD-key, it begins the installation and then keeps telling me to Please mount the Unreal Tournament 2004 Play Disc CDROM. Unmounting and remounting the disc does not work. 

While running Gutsy (7.10) the installation worked fine by simply running: 
```
sudo ln -s /media/cdrom0 /media/dvd
export SETUP_CDROM=/media/dvd/
mount /media/cdrom0 
sudo sh /media/cdrom0/linux-installer.sh
```
as mentioned in another thread on this forum: [http://ubuntuforums.org/showthread.php?t=729319]("http://ubuntuforums.org/showthread.php?t=729319")

This time, it fails running it any way that I've tried. I saw the post by AWalton at [http://ubuntuforums.org/showthread.php?t=729319]("http://ubuntuforums.org/showthread.php?t=729319"), and I've taken those steps and more. Not only have I told the system to do nothing when any device is connected, I've also tried selecting the "Never prompt or start programs on media insertion" option within Nautilus >> Edit >> Preferences >> Media tab. 

So, it's not just autorun, it's automount I am having a problem with. How do I disable the automount feature in ubuntu 8.04 hardy heron?

---

### Post by bmac on 2008-04-28
In the configuration editor:
apps/nautilus/preferences/media _ automount

Multiple choices... Including "never"

---

### Post by rubicon on 2008-04-28
You can also stop hal ```
sudo /etc/init.d/hal stop
```to stop hardware detection completely, but this is not recommended.

But is this what you realy want to do? :)

---

### Post by gaebriel on 2008-04-28
Thanks guys. Looks like the gconf-editor option is a go. You're right that I don't want to disable hardware detection, but I found I could run ```
hal-disable-polling --device /dev/scd0
``` if I want to narrow the scope, which is something I might want to do. :) 

Turns out these didn't help my ut2004 installation problem though. I went back to an older thread ([http://www.backports.ubuntuforums.org/showthread.php?p=4819407]("http://www.backports.ubuntuforums.org/showthread.php?p=4819407"))I used with gutsy to get ut2004 installed and found someone else stumbled upon the solution for installing it in hardy. Seems you have to mount the cd as an ISO9660 image instead of the default UDF. Then it works. Thanks again guys, as I will have need of disabling automounting in other situations I'm sure and this thread will come in handy later. :)

---

### Post by antti64 on 2008-06-16
> **bmac said:**
> In the configuration editor:
apps/nautilus/preferences/media _ automount

Multiple choices... Including "never"

This doesn't work for internal harddrives. How to disable automount of internal harddrives? I'm having problems in boot-up because system runs e2fsck for my /home directory, which is already mounted. 

Antti

---

### Post by dcstar on 2008-10-21
> **antti64 said:**
> This doesn't work for internal harddrives. How to disable automount of internal harddrives? I'm having problems in boot-up because system runs e2fsck for my /home directory, which is already mounted. 

Antti

Internal drive are mounted by /etc/fstab - and that also has scan on boot settings.

---

