---
title: "GRUB Error"
date: 2006-07-11
forum: General Help
---

### Post by metallcoholix on 2006-07-11
I used to have ubuntu and windows running in my system, I formatted my machine this afternoon and wanted to switch to only windows, after formatting all the partitions and installing windows succesfully I restart the machine, and everytime i turn it on a message saying GRUB loadins, please wait...
Error 17, a while ago the erros 22 appeared, anyways, i cant log in to windows or ubuntu because of this, any help???

---

### Post by scxtt on 2006-07-11
if you've got a boot floppy (for windows) i think you can do:
[indent]A:>format /mbr[/indent]to clear the master boot record ... don't know if this'll "hide" windows install as well, i don't think so ... you might also be able to do this w/ a bootable windows install disk ...

check this link/post out:
[http://www.ubuntuforums.org/showpost.php?p=1243180&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1243180&postcount=2)

---

### Post by hanzomon4 on 2006-07-11
I found some info on the gentoo forums concerning grub errors
> Grub error 17

info grub wrote:
17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.
Be sure to check your root(x,y) settings in your grub.conf.



here is the [link]("http://forums.gentoo.org/viewtopic.php?t=122656")

---

### Post by firezip on 2006-07-15
So how can I do this?

(I'm new to the whole Grub thing)

Also is there an easier Alt. to grub?

---

### Post by Herman on 2006-07-16
>  Also is there an easier Alt. to grub?  GAG Boot Manager is a Graphical boot manager which can be run form a CD, floppy disk or installed to MBR. GAG is easier to use, and faster to re-configure if you change operating systems or hard disks often.  [***Click Here***]("http://users.bigpond.net.au/hermanzone/p12.htm") for more on that. GAG Boot Manager makes a good emergency boot disk for Windows too, anyone who install Linux should have one.

Another solution is to re-install Ubuntu just on a minimal sized partition, for example just on 2 or 2 1/2 GB of your disk. You won't miss such a small amount of disk space and you never know when Ubuntu might come in handy for something, even if you don't use it at all in the meantime.
You can '[hide the grub menu]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu")', and [set default operating system to Windows]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc"), and [set the timer down to 2 or 3 seconds.]("http://users.bigpond.net.au/hermanzone/p15.htm#timer") (Or even down to 1).
You will not even remember Ubuntu is in your computer until someday when you need it.

Or, if you really want to, uninstall Ubuntu (and GRUB) [***Click Here***]("http://www.users.bigpond.net.au/hermanzone/p18.htm") for details.

---

### Post by [S|G] on 2006-07-16
If you need to reconfigure your grub, you'll need basically to edit your /boot/grub/menu.lst:
```

sudo nano /boot/grub/menu.lst

```
Then check your partitions to see if they match your actual disk layout. To make things easier for you, paste your menu.lst and the output of this command:
```
sudo fdisk /dev/hda -l
```
If your hard drive is not /dev/hda, change it to match it (/dev/hdb, /dev/hdc, /dev/hdd).

---

### Post by firezip on 2006-07-16
> **'[S|G] said:**
> If you need to reconfigure your grub, you'll need basically to edit your /boot/grub/menu.lst:
```

sudo nano /boot/grub/menu.lst

```


When I do this it appears that the grub menu list is empty.

[http://img100.imageshack.us/img100/9823/screenshotcd0.png](http://img100.imageshack.us/img100/9823/screenshotcd0.png)

---

### Post by [S|G] on 2006-07-16
One user reported that in his system the file was actually called "/boot/grub/menu.list". You could try that in your system to see if it works.

---

### Post by firezip on 2006-07-16
I have a 250gb hd. I read somewhere you need to create the first 2 partitions on the first 1024 cylinders. The problem is I don't want 16gb of free space(I want the full 80gb I originally assigned)

---

