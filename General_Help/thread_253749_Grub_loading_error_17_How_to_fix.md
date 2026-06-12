---
title: "Grub loading error 17: How to fix?"
date: 2006-09-08
forum: General Help
---

### Post by link141 on 2006-09-08
First of all, thanks to anyone in advance for reading this.  I have a home built computer with modern parts in it.  I *had* the main  hard-drive partitioned with a 43GB NTFS partition for windows and 43GB for Kubuntu (swap & ext3, 80GB drive with bad sectors).  As far as I know, everthing is compatible with Kubuntu except for the integrated graphics and audio on the store-bought Mother board (bizare Via-S3G hybrid Unichrome-Pro Graphics chip, and C-media Audio chip).  Here's what did it in: I was running an activated copy of Windows on my computer along with a version of Kubuntu Dapper (windows stinks) when the windows side began getting bogged down with crap.  This is inevitable for Windows because of it's poor quality programing and application incompatibilities, therefore, even Microsoft recommends periodically reinstalling Windows on your machine.  Because of how messy it was, I just decided to back up my data, erase the hard-drives, partition them, and start with a fresh copy of both OSes (at this point Kubuntu was a "sandbox" copy to see if I liked it).  All went well except for Windows *rejecting* the product key I was given, because it will only let you reinstall it *three* times with the activation key.  I'm sorry for complaining, I only paid 200 dollars for it with my other computer, and microsoft is entitled for ripping you off as many times as they want for something you *bought* from them.  

So, a month passed, and I used mostly Kubuntu during this time, but when I needed to use windows on the last of the 30 days your allowed to use it, it told me I had activate it with in one day, or it would lock itself out.  I didn't care much because I don't like windows, and used Kubuntu instead.  

The next day, after I used Kubuntu once and booted up again, grub gave me this message: 
```
Grub loading stage 1.5

Grub loading error 17 
```
I did some searching booting with this live CD, and found that this occurs when Grub becomes confused and can't find it's boot locations.  Windows should let you boot, even when it's locked out, like it did the day before.  I checked my hard-drive with my G-parted live CD, and **all** of my main disk space was shifted to Kubuntu, and the NTFS partition was **gone**.  I hypothesize that when windows becomes deactivated, it must cloak itself on the hard-drive so you can't mess around with it using some third-party application, or deletes itself completely.  Microsoft didn't do this in a way to run another OS safely on the same computer, or a way you could get your data off that partition, because, of course, when your running Windows, your computer know belongs to Microsoft.  The $%^@^&@ NTFS partition must have been invisible to Kubuntu, and written over, or more likely deleted itself when I didn't activate it immediately.  

The Windows side of the computer is gone, along with all my data on that partition, but the Kubuntu Partions are still there, and hopefully the data on them is okay.  All I want is a way to look through the data on the ext3 partition, and copy the data I want on to an external USB hard-drive.  I can "see" the partition from this live CD, but can't mount it and view the data on it because of this error: mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab.  Anyone have any ideas?  Thanks :)!

---

### Post by Jose Catre-Vandis on 2006-09-08
You are getting the mount error because either

a) you are not using sudo
```
sudo mount /dev/hda1 /mnt/drive1
```
b) you need to create a directory to mount the /dev/hda1 to
```
sudo mkdir /mnt/drive1
```

Also look at this page for directions on how to reinstall grub
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by link141 on 2006-09-08
Thanks!  The error is probably because of b, because I was using the kdesu command to run konqueror.  I'll try that though...  Thanks again :)!!

---

