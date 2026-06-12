---
title: "Adding Second Hard Drive for Storage"
date: 2017-07-06
forum: General Help
---

### Post by daniell59 on 2017-07-06
I would appreciate it if somebody could simplify  this for me. I am almost out of Hard Drive space. I would like to add another hard drive for storage. I have already read how to do it, but for some reason I am confused.

Ubuntu 14.04 32

---

### Post by deadflowr on 2017-07-06
What are you confused about?

---

### Post by daniell59 on 2017-07-06
> **deadflowr said:**
> What are you confused about?

First off I want to make sure that I format the proper drive. Also, What file system should I use?

---

### Post by CatKiller on 2017-07-06
> **daniell59 said:**
> First off I want to make sure that I format the proper drive. 

Yes, you definitely do.

> Also, What file system should I use?

It depends. If you're going to want to access it from Windows, use FAT32 or NTFS. If you're only going to access it from Linux, ext4 is a perfectly fine choice.

---

### Post by daniell59 on 2017-07-06
I am somewhat confused when it comes to making a mount point for the new drive. I would appreciate it if somebody could explain to me how it is done.

---

### Post by oldfred on 2017-07-06
If permanent mounting with fstab you need to create a mount point, give yourself ownership & permissions if a Linux formatted partition, and add an entry to fstab. Best just to use an example or template with your data like UUID and mount point.
If only occassionly using it, you can give partition a label and in Nautilus it will show as that label. If not labeled it may show by UUID and then you are not sure which is which if mounting multiple partitions.
Generally temporary mounts are in /media & permanent mounts are in /mnt, but many discussions on mount locations. You can also directly mount in /home if desired.
Mounts in /media or /home will show in Naultius left panel, but /mnt will not. I use /mnt but then link folders in my data partition into /home to easily see or use them.
Linux gives lots of flexibility, With Windows you get a d: "drive" or partition.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[URL="https://wiki.archlinux.org/index.php/Fstab"]https://wiki.archlinux.org/index.php/Fstab

[/URL]
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 

If also wanting to link folders into /home.

 [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) 

[URL="https://wiki.archlinux.org/index.php/Fstab"]
[/URL]

---

### Post by daniell59 on 2017-07-06
I am sorry to admit it but until now I never heard of fstab. This is all new to me.

---

### Post by oldfred on 2017-07-06
You only need to edit fstab if you want to permanently mount a partition.
But you have to click on it in Nautilus or manually mount after a reboot to remount if not mounted via fstab.

---

### Post by daniell59 on 2017-07-07
> You only need to edit fstab if you want to permanently mount a partition.
But you have to click on it in Nautilus or manually mount after a reboot to remount if not mounted via fstab.

Thanks for the information. I will keep reading until it sinks in.

---

### Post by ra7411 on 2017-07-07
I've added HD's to my desktop machines, and I think it was a fairly simple process - BUT GO SLOW AND CAREFUL. 
If I've forgotten or botched anything below somebody should correct it ASAP.

First, have Gparted installed on your machine.
Then shut down and power off by unplugging the power cord and shutting off any batts.
Avoid static discharge from your hands to the machine by touching something metal before touching your HD or mobo.
Hook up the HD power cable and the the data cable from the mobo to the HD. 
Then start the machine. 
Start up Gparted, let it find your new HD.

MAKE SURE YOU THEN PROCEED ON THE NEW DRIVE, NOT ONE YOU ALREADY HAVE PROGRAMS  AND DATA  ON.

Create one or more partitions on the *NEW* HD. 
    This will not be a happy experience if you inadvertantly destroy existing partitions you have been using - you will then enter a computer purgatory where you scramble to try to make things like they were before you started all this....

For Ubuntu partitions I think you will probably want file system ext4. For any partitions that Windows will be using probably NTFS.

---

### Post by daniell59 on 2017-07-07
> **ra7411 said:**
> I've added HD's to my desktop machines, and I think it was a fairly simple process - BUT GO SLOW AND CAREFUL. 
If I've forgotten or botched anything below somebody should correct it ASAP.

First, have Gparted installed on your machine.
Then shut down and power off by unplugging the power cord and shutting off any batts.
Avoid static discharge from your hands to the machine by touching something metal before touching your HD or mobo.
Hook up the HD power cable and the the data cable from the mobo to the HD. 
Then start the machine. 
Start up Gparted, let it find your new HD.

MAKE SURE YOU THEN PROCEED ON THE NEW DRIVE, NOT ONE YOU ALREADY HAVE PROGRAMS  AND DATA  ON.

Create one or more partitions on the *NEW* HD. 
    This will not be a happy experience if you inadvertantly destroy existing partitions you have been using - you will then enter a computer purgatory where you scramble to try to make things like they were before you started all this....

For Ubuntu partitions I think you will probably want file system ext4. For any partitions that Windows will be using probably NTFS.

Thanks for your informative reply. I understand everything that you have written. The next steps get me confused. Mounting and adding a line.

---

### Post by Autodave on 2017-07-07
If you are only going to store stuff on it like pics, documents, scans, etc, then install the drive as previously outlined, boot machine and use gparted to create a partition covering the entire drive, format to NTFS.  After all that is done, you will see an icon on your screen for the drive, but it will be grayed out. Double=clicking will mount and open it for you. Then, youi will be able to create folders on it to move your pics, docs, etc to from your current drive.

---

### Post by scpatl4now on 2017-07-07
If i has not been mentioned, I think the easiest way (and using a GUI) is to go to your applications and search for
disks
It will bring up a list of hdd.  you can format it there and also by clicking the little gear in the lower left side and got to edit mount options you can make the task easier (I'm not sure how to get photos to show but here are links to screen shots

[https://goo.gl/photos/tRdFq7wx4TPxEcUk9](https://goo.gl/photos/tRdFq7wx4TPxEcUk9)

[https://goo.gl/photos/guAod7yfHycHyYmNA](https://goo.gl/photos/guAod7yfHycHyYmNA)

---

### Post by ra7411 on 2017-07-07
a Disks program pic is attached, the square, dash and gears have menus, I think the square mounts the HD.

---

### Post by deadflowr on 2017-07-07
> **ra7411 said:**
> a Disks program pic is attached, the square, dash and gears have menus, I think the square mounts the HD.

Square means already mounted.
An arrow (playback-like button) means can be mounted, but isn't.
Nothing (no symbol) means cannot be mounted, typically what you see with an Extended partition.
(You cannot mount an extended partition, but you can mount the underlying logical partitions that the extended partition contains.)

---

