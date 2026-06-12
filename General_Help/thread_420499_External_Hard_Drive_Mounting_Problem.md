---
title: "External Hard Drive Mounting Problem"
date: 2007-04-23
forum: General Help
---

### Post by number3pencil on 2007-04-23
Upon upgrading to Feisty, I have had a problem getting my external to mount.  When I plugged it in, it showed up under /media, but when I tried to access it I got a 'hal-storage-removable-mount-all-options refused uid 1000' error.  After tinkering around with fstab and other things, now I do not get an error, it mounts the drive but says theres nothing in it.  Here's my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fcde0cec-4a9d-4f21-9a2a-9c79335f0baf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=54a62178-b39a-48f4-826d-5cc43c0f797b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

The stupid thing is when I do a pmount sdb5 it mounts and all of the files are viewable and accessible.  How can I get Kubuntu to correctly automount my external?  Any help greatly appreciated.

---

### Post by GoodPanos on 2007-04-23
Same problem here.  Have fresh install of Kubuntu Feisty Fawn and have installed also NTFS-config and it does not auto-mount.  My WinXP partition works fine but that has an entry in FSTAB.

Auto-mount worked fine in Ubuntu Feisty Fawn.

It looks like there is a bug.  Any help is appreciated.

---

### Post by ujecrh on 2007-04-24
Same problem here ( 'hal-storage-removable-mount-all-options refused uid 1000' )

By the way, digging a bit I also noticed that the Feisty souces of pmount do not contain the patch to support ntfs-3g. It is not the reason for the above issue but it would be nice (and easy) to fix this too.

---

### Post by soulfly7x on 2007-04-24
I have either the same or a similar problem since my upgrade to Kubuntu Feisty. It does not mount my external hard drive. I can get to **/media/WD External USB 2.0**, if I look in the folder it's blank. I don't get any error message though.  At the bottom of the window in Konqueror it says, "No Items - No Files - No Folders."

If I reboot into the Ubuntu Edgy partition, the external drive mounts fine, reads, writes, shows up on the desktop, does everything it's supposed to do. I need access to the external drive because that's where I keep all my files so I have access no matter which partition I boot into, or even if I'm on my laptop instead of the desktop, so this bug is particularly annoying.

Sorry I don't come bearing a solution, I'm just a n00b myself. I just know it worked before the upgrade, and now it doesn't.

---

### Post by GoodPanos on 2007-04-24
Well, for now if you want to do it manually here's what you do (assuming you have ntfs-config installed):
```
fdisk -l
```
That will give you a list of attached HD devices, i.e. /dev/sdb1.
Then type:
```
sudo mkdir /media/<name of device>
```
<name of device> is the name of your external HD you want to give it.  Then
```
sudo mount -t ntfs-3g /dev/sdb1 /media/<name of device> -o nls=utf8
```
That will put an icon on your desktop of your external HD.  Now you can open your HD and have read/write access.

Once again though, this should work automatically after you have set up ntfs-config.  I know it works in Ubuntu Edgy Eft and Feisty Fawn and Linux Mint Bianca KDE, but for some reason not the latest Kubuntu.

---

### Post by capdog on 2007-04-27
Same problem here. Did you guys use Automatix by any chance? There was an option in there to make all NTFS drives mount under NTFS-3G. Maybe that broke it?

Kubuntu rules though...

---

### Post by madonion87 on 2007-04-27
yea ive just installed a fresh copy of feisty today and automatix ntfs auto mounter
after that my internal harddrives works ok
but my external harddrive doesnt

---

### Post by soulfly7x on 2007-04-27
**capdog** > Did you guys use Automatix by any chance?

I can't speak for the others, but I used > sudo apt-get install ntfs-config

**GoodPanos**, I'll try that when I get back home. I'll let you know if it worked. Thanks.

---

### Post by soulfly7x on 2007-04-30
It's definitely a bug with the system. I realized that the ntfs-config is for enabling *writing* to the NTFS drive, but Kubuntu should be able to *read* from it even without ntfs-config installed.

I popped in a live CD of Kubuntu Edgy and was able to access the external drive, but Kubuntu Feisty just plain won't see it.

---

### Post by ujecrh on 2007-05-06
Still no update on this bug?

---

### Post by iainblack on 2007-05-06
Just to agree with the above and that sometimes CD's don't remount after I eject/insert new ones. Also, not sure if it is related, but I am having trouble with VMWare server and ISO/CD's booting. Not sure if this is related but thought worth mentioning. Anyone else having similar issues?

---

### Post by capdog on 2007-05-07
Did anyone submit a bug report or know of an existing report?

---

