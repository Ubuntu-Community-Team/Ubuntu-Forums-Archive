---
title: "[SOLVED] Dual/multi boot"
date: 2008-06-16
forum: General Help
---

### Post by achelis on 2008-06-16
Hi

I'm currently running Ubuntu 8.04 (64-bit) but would like to try both the 32-bit version and Kubuntu. The reason I'd like to try 32-bit is that there is quite a few compatibility issues which I'm hoping is due to 64-bit.

Rather than format and reinstall everything I was hoping to be able to simply create a new partition for ie. Kubuntu and install it there. Then mount the old home-partition when booting either Ubuntu or Kubuntu - I'm thinking this should be achievable but is it a good idea?

Also when installing Kubuntu I'm thinking I will loose my Grub setup, but is there other things to look out for concerning loss of data?

I have unpartioned space on my hard-drive so making a new partition shouldn't be a problem. Also I think I only need one swap-partition which can be used by both Ubuntu and Kubuntu ?

Hope someone can help me on my way.

---

### Post by logos34 on 2008-06-16
> **achelis said:**
> Hi

I'm currently running Ubuntu 8.04 (64-bit) but would like to try both the 32-bit version and Kubuntu. The reason I'd like to try 32-bit is that there is quite a few compatibility issues which I'm hoping is due to 64-bit.

Rather than format and reinstall everything I was hoping to be able to simply create a new partition for ie. Kubuntu and install it there. Then mount the old home-partition when booting either Ubuntu or Kubuntu - I'm thinking this should be achievable but is it a good idea?

The simplest way would be to install the kde desktop alongside ubuntu gnome:

sudo apt-get install kubuntu-desktop

Then choose either at the login screen.

But this will be the 64-bit version.

You'll have to install x86 version to the other partition.  I wouldn't try to share /home.  (If there's anything you want to save, save it to ubuntu /home. (use symlinks or something)

> Also when installing Kubuntu I'm thinking I will loose my Grub setup, but is there other things to look out for concerning loss of data?

At the "Ready to Install' screen, hit 'Advanced' button lower right and change default '(hd0)' to /dev/sda?, where ? = kubuntu root partition.  This will put it on the bootsector of the kubuntu root, thus preserving ubuntu grub on the mbr.  Then just [add a kubuntu entry]("http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink") to ubuntu grub /boot/grub/menu.lst.

> I have unpartioned space on my hard-drive so making a new partition shouldn't be a problem. Also I think I only need one swap-partition which can be used by both Ubuntu and Kubuntu ?

yes.

---

### Post by achelis on 2008-06-16
Thanks a lot. Kubuntu installed on its own partition now and a boot option added to my menu.lst and everything seems to be working perfectly :)

> 
 I wouldn't try to share /home. (If there's anything you want to save, save it to ubuntu /home. (use symlinks or something)


I'm not quite sure what you mean. Possibly because I'm not familiar with symlinks.. So far I haven't shared home. Should I have separate home-partitions for the separate installations? And then have a common partition for data ? If you will elaborate on what you mean I would be most grateful, and thanks again for the help!

---

### Post by logos34 on 2008-06-16
maybe I misunderstood you--when you said 'old home-partition' I thought maybe you had /home on a separate partition instead of on ubuntu root. Please clarify.

64-bit ubuntu and kubuntu will/can share existing /home (whether separate or on /).  Just do a default install 32-bit kubuntu on the other partition (no separate /home).
A common data partition would be ok, or just use the ubuntu home directory to save any downloads, documents, music, etc. while in kubuntu. The latter should detect ubuntu and add it to fstab so it automounts at '/media/sda?'.  If not [see this]("http://www.psychocats.net/ubuntu/mountlinux").

Adding symbolic links in the 32-bit kubuntu /home directory just makes it easier to save stuff to your master home, multimedia dump partition, etc.  For instance, I'm running a 32-bit Mandriva test partition, and I have 'music', 'downloads' etc. pointing to directories with the same name in my separate master /home partition (Ubuntu Studio 8.04 x64) and huge /music partition .


See **man ln**

---

### Post by achelis on 2008-06-17
Ok I think I got it.

So I have:
/dev/sda1 : 64-bit root / boot partition
/dev/sda3 : 64-bit /home
/dev/sda6 : 32-bit root / boot and home.

And then I mount sda3 in 32-bit as something else than home and create links to the data-directories for easy access?

---

### Post by logos34 on 2008-06-17
> **achelis said:**
> Ok I think I got it.

So I have:
/dev/sda1 : 64-bit root / boot partition
/dev/sda3 : 64-bit /home
/dev/sda6 : 32-bit root / boot and home.

And then I mount sda3 in 32-bit as something else than home and create links to the data-directories for easy access?

ok, so I did understand you right the first time--you do have a separate /home.
(
Before (or after) you install 32-bit kubuntu, add this to bottom of ubuntu menu.lst so you can select kubuntu from ubuntu grub menu:

gksudo gedit /boot/grub/menu.lst (or sudo nano /boot/grub/menu.lst)

> 
title		Kubuntu 8.04 (32-bit)
root		(hd0,5)
kernel		/vmlinuz root=/dev/sda6 ro quiet splash
initrd		/initrd.img

('/vmlinuz' and '/initrd.img' because it's using the symlinks in the root dir--that way you won't have to edit it after a kernel update)

If 32-bit kubuntu doesn't add an entry to its fstab for sda1 to automount, simply do this this:

sudo mkdir /media/sda1

kdesu kate /etc/fstab (or, if you prefer, sudo nano /etc/fstab)

> /dev/sda1 /media/sda1 ext3 defaults 0 2

or uuid format:

> # /dev/sda1
UUID=xxx-xxx-xxx... /media/sda1 ext3 defaults 0 2

(copy the UUID from fstab on sda1)

Ditto for sda2 /home.

Let's say you want to have any downloads in 32-bit kubuntu saved to download folder in ubuntu /home:

ln [OPTION]... TARGET... DIRECTORY     (3rd form)

ln -s /media/sda2/downloads downloads 

etc.

Since sda1 is a root/system partition, be careful not to change permissions  & ownership recursively ('-R')...Apply chown and chmod to mount point ('/media/sda1') only.

It seems more complicated than it really is.

Good luck!

---

### Post by achelis on 2008-06-17
Thanks again. I think I got it now :)

I see no reason to mount sda1 though as it's only the 64-bit Ubuntu specific stuff lying there. So I'd probably just risk messing something up if I did.

I'll have to play around a bit more to get the symbolic links working.

---

### Post by logos34 on 2008-06-17
> **achelis said:**
> Thanks again. I think I got it now :)

I see no reason to mount sda1 though as it's only the 64-bit Ubuntu specific stuff lying there. So I'd probably just risk messing something up if I did.

I'll have to play around a bit more to get the symbolic links working.

Yeah, it probably would be best to not mount sda1 unless you have to.  So just apply the instructions for sda2 /home

---

