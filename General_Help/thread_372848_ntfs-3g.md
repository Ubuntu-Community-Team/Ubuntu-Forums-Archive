---
title: "ntfs-3g"
date: 2007-02-28
forum: General Help
---

### Post by awtomlinson on 2007-02-28
I am using Ubuntu 6.06.  I have an external USB hard drive (enclosure) with an NTFS partition.  I used this guide to setup ntfs-3g:  

[http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/](http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/)

I completed the following steps without realizing that I wasn't finished:

[B]these commands to add the repository to your “sources list :

gksudo gedit /etc/apt/sources.list

#ntfs-3g & fuse-2.5 repo:

deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main

deb-src [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main

From there download & install the .deb driver. In the terminal type:

sudo apt-get update && sudo apt-get upgrade

sudo apt-get install ntfs-3g[/B]

Using fdisk -l, my external hard drive displayed as both /dev/sda2 & /dev/sda5 for some reason, even though it is only 1 partition.  I had full read access to the drive, but no write access.  However, after completing the following steps, the external drive is no longer detected:

[B]Now add your NTFS drive to your fstab file, so it will be loaded on boot up :

Open your teminal and type:-

gksudo gedit /etc/fstab

Add this to the bottom:-

/dev/partition /media/mount point ntfs-3g silent,umask=0,locale=en_US.utf8 0 0

Mine looks like this :-

/dev/hdc1 /windows ntfs-3g silent,umask=0,locale=en_US.utf8 0 0

*NOTE* Even if you already have your NTFS partition mounted, DO NOT forget to change this part. It is DIFFERENT.

Now you need to add Fuse to your modules file so it can be loaded on boot up :

gksudo gedit /etc/modules

Add fuse to the bottom of the file

Now you can either reboot and the drive will be mounted or you can try mounting it without rebooting by typing this command in the terminal :

sudo modprobe fuse

sudo umount -a

sudo mount -a[/B]

Now, the drive is not detected at all, even after commenting out the section in the fstab file.  Can anyone help me with getting Dapper to once again recognize this drive & allow me read & write privileges?

---

### Post by garybrlow on 2007-02-28
Do not use ntfs-3g tutorials other than the ones found here and pointed out at the NTFS3g official page [http://www.ntfs-3g.org](http://www.ntfs-3g.org) they are not updated unless they are of course. Ntfs-3g has changed a lot since then (it has come out of beta and become stable) and the installation has slightly changed. You now have two options 1)using the usual but with compilation for new fuse versions and 2)using ntfs-config program. The first method is manual while the second one is automatic, I suggest using the 2nd method because it quicker and easier. Refer to this thread, this is the official ntfs-3g thread for (X/K/Edu)Ubuntu [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009). Recheck your procedure, the new ntfs-3g requires Fuse 2.6 above, refer to the link given above.

Cheers!!! :popcorn: 


GaryBrlow :biggrin:

---

### Post by bodhi.zazen on 2007-02-28
ntfs-config : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

Shorter and more automagic ;)

---

### Post by awtomlinson on 2007-02-28
Like I said before, Ubuntu 6.06 no longer even detects my external drive.  Any ideas?

---

### Post by bodhi.zazen on 2007-02-28
???

Disconnect and reconnect the drive.

Wait a few seconds (30)

Post the output of ```
sudo fdisk -l
```

---

### Post by awtomlinson on 2007-02-28
Got it working, many thanks.  I simply rebooted into Windows XP (sigh) & used the Safely Remove Hardware feature, rebooted into Ubuntu, & now I have full write access.  Thanks again!!!

---

