---
title: "Ubuntu not loading after GRUB"
date: 2013-06-09
forum: General Help
---

### Post by Kymus on 2013-06-09
An odd thing happened. I was on call on Skype, and well, for some reason that thing loves to crash my PC whenever I do video chat.. but anyway, it froze up, I rebooted, went in to GRUB, attempted to load Ubuntu and... nothing. It'll go through some steps (I have no idea what  they are), the login will flash for a brief second, and then it just hangs after that. I've got no idea what is going on.

addendum: this is 13.04 (I need to change my version # on here..)

---

### Post by Kymus on 2013-06-10
bump.

---

### Post by oldfred on 2013-06-10
If system crashed it may have an issue with partition that a fsck would fix.

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by Kymus on 2013-06-14
Hi oldfred, thanks for your help.

I booted in to Ubuntu from usb (I saw no option to boot to terminal), opened the terminal, ran  sudo e2fsck -C0 -p -f -v /dev/sdb1

and I got the error that sdb1 wasn't found.. so I tried sdb2 and sdb3 for the hell of it. Nothing.

Where did I screw up?

---

### Post by oldfred on 2013-06-14
My example is sdb1, but you have to use your partitions and they must be the ext2, ext3 or ext4 formatted partitions.

If unsure of which partitions you can run this and it will show which format & UUID.

sudo blkid -c /dev/null -o list

Part of mine (its long):

```
fred@fred-Precise:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    (not mounted)  04B05B70B05B6768
/dev/sda2  ext3    backup   (not mounted)  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdb1  vfat    EFI32    (not mounted)  2404-8A43
/dev/sdb3  ext4    sys      /media/sys     e2156d09-329e-4262-9549-f72a05d97f93

```

---

### Post by Kymus on 2013-06-15
Ok, I got fsck to run fine, and after it was done, I rebooted, loaded Ubuntu normally from GRUB, and..... same thing. It just hangs.

It does some stuff after directly telling it to load, and then a login screen (in the terminal, not in the GUI, just to clarify) will flash for a few seconds, then the screen will basically go black and it just hangs there. I watched the data light and it blinks a couple times in the first minute and then after that it just does nothing; there doesn't seem to be any activity.

---

### Post by oldfred on 2013-06-15
That sounds like a video issue of some sort.

I was just updating my Saucy install and have exactly the same error, but it is still in development & I am sure my nVidia is not configured correctly as I has copied Raring into Saucy and I do not think it updated driver.

Did you update video or change video drivers?

---

### Post by Kymus on 2013-06-15
Not to my knowledge, no.

I mean, I don't often reboot my system or otherwise exit out of Ubuntu, so unless it just happened to have updated itself along with the other updates that occur, then no, nothing was updated.

---

### Post by Kymus on 2013-06-15
addendum: to my knowledge, there was no prompt present to reboot my system (to finish an update) at the time my system was last running (I could be wrong... but I don't think I am). So I think the likelihood of a video update of some sort I would say is slim.

---

### Post by oldfred on 2013-06-15
Try recovery mode, if you have several kernels it will be under Advanced Options.

---

### Post by Kymus on 2013-06-15
OK, I think we're getting somewhere.

First I ran the oldest one: 2.6.38-12 generic (recovery mode)

when prompted I told it to resume a normal boot.

This loaded Ubuntu's login screen (the GUI). I didn't bother experimenting past that point since - as I was warned - the graphics were wonky.

So then after this, I rebooted again and now loaded 3.8.0-19-generic (recovery mode)

Same as before, I told it to resume normal boot.

This time, at the login (in the terminal/CLI) there was an error:

**shoaxing login: initctl:event failed**

Then it just goes black and does nothing.

---

### Post by oldfred on 2013-06-15
This user said he reinstalled video drivers & errors went away.

[http://askubuntu.com/questions/248986/ubuntu-12-04-lts-no-longer-able-to-boot-normally](http://askubuntu.com/questions/248986/ubuntu-12-04-lts-no-longer-able-to-boot-normally)

Be sure to shut down correctly or else you will have to do a full fsck from a liveCD.

 Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

