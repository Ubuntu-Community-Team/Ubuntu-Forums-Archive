---
title: "dd bootable clone question"
date: 2020-12-09
forum: General Help
---

### Post by ra7411 on 2020-12-09
I have a desktop with an ssd sda (/ and /home) and an sdb HD which also has a Ub o/s on it.


I want to use dd to make a backup bootable clone of my 500gb sda onto a 2tb HD (sdc) which I'll hook up with sata cables.


1] in the event of a recovery from the 2tb HD clone to the 500gb ssd, it should work ok, right?


2] instead of creating the clone through a live usb "try ubuntu" route, I'd prefer just using the existing o/s on sdb. That should work, right?


3] what condition does the target sdc need to be in? Mounted, unmounted, unallocated, unformatted or what?


4] what condition does the source sda need to be? Unmounted, mounted or what?


5] In the above setup the terminal command while in the sdb o/s would be 


sudo dd if=/dev/sda of=/dev/sdc   right?


Is there anything I'm not covering here, or any problems to watch out for?


Thanks

---

### Post by SeijiSensei on 2020-12-09
All the devices need to be unmounted. Boot from a USB stick created from a distro ISO file.

I've only ever used dd, or more accurately ddrescue ("sudo apt install gddrescue") to clone drives of equivalent size.

An alternative is to use the dpkg directive --get-selections to build a list of installed software. Then create a new Ubuntu installation using the same version (e.g., 20.04) on the target drive and use --set-selections to install any missing packages. See "man dpkg" for details.

---

### Post by oldfred on 2020-12-09
The dd is not considered the best way to backup a drive.
With dd, you should be using exact size drive to exact size drive. And it copies all the unallocated empty space, so slow.
You also then cannot reboot with both drives connected as duplicate UUID/GUIDs are not allowed.

discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) & 
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)

Most that want image backups suggest clonezilla.
But image is obsolete as soon as you use system and most do not then regularly run image backups.

Ubuntu is relatively easy to install, so often quicker & easier to just backup your /home, list of installed apps, perhaps some settings in /etc and if you have installed any server type apps that have folders in / (root) back those up. 
This is exactly what you do if your hard drive fails & lets you automate backup so it is more current.

Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

---

### Post by ra7411 on 2020-12-09
>[COLOR=#000000] drives of equivalent size.<[/COLOR]

Right, a dd restore from a 2tb will try to copy all the empty space into the 500gb.

---

### Post by VMC on 2020-12-09
I would never use dd. Instead fsarchiver or CloneZilla. Both backup used sectors only. Much faster, safer than dd. Don't use fsarchiver on ntfs partitions.
I've never had issue with backup/restore using either fsarchiver/clonezilla.

---

### Post by C.S.Cameron on 2020-12-09
> **ra7411 said:**
> 

5] In the above setup the terminal command while in the sdb o/s would be 

sudo dd if=/dev/sda of=/dev/sdc   right?



This will overwrite **everything** on your target drive.

I prefer creating clone image file using Gnome-Disks from a Live USB. The resulting image can be zipped to save space.

Some people prefer Clonezilla.

---

### Post by ra7411 on 2020-12-10
[COLOR=#000000]>This will overwrite [/COLOR]everything on your target drive.<

I know that.
 I have several 2tb hd's sitting around unused. My main machine has ub 18.04 on a 500gb ssd with numerous apps that consume a lot of time re-installing and re-setting. If that install fails, or I want to put it onto either of my 2 auxillary desktops, I want a plain way of creating bootable clones onto those unused 2tb's. From what I've read, dd is a reliable uncomplicated way of doing that.

>I prefer creating clone image file using Gnome-Disks from a Live USB. <

I have an sdb drive on the source machine with Ub  18.04 on it. Do I need to use a live usb to work through, or would the sdb o/s be ok?

---

### Post by C.S.Cameron on 2020-12-11
As you show it, dd will overwrite the whole 2TB sdc drive leaving a lot of unformatted space, (1.5TB). This is okay if you want a duplicate cloned drive for backup, but a bit of waste if you just need an image that you can restore when needed.

 Gnome-Disks will just make an image file the size of sda. The image file can be truncated and/or zipped to reduce space.

If you are not cloning data from sdb, it is fine to use that to run the cloning operation from.

---

### Post by dinkidonk on 2020-12-12
I've used dd to make bootable clones a couple of times and never had any issues with it. If you want to save a copy of a (bootable) drive in order to be able to restore it, you can compress it to save space like this:

```
#Backup
dd if=/dev/sda | gzip > /path/to/compressed/image.gz

#Restore
dd if=/path/to/compressed/image.gz | gzip > /dev/sda
```

Works great! :-)

---

