---
title: "clone copy hard drive so it boots identical to original"
date: 2012-10-29
forum: General Help
---

### Post by sdowney717 on 2012-10-29
Want to make a backup drive that is the exact image of the installed drive. This will be so that if the original drive fails, I can replace with the clone and immediately run PC again on the boat.

what is best way to do that?
both drives are 60gb size.

I was also thinking perhaps putting a toggle switch on the PS for the drives. Leave the data cables plugged in and turn off bad one and turn on cloned drive if a problem occured. Would the PC boot from a slave drive?

---

### Post by dino99 on 2012-10-29
not only your question, but

[http://askubuntu.com/questions/62340/how-to-copy-an-ubuntu-install-from-one-laptop-to-another](http://askubuntu.com/questions/62340/how-to-copy-an-ubuntu-install-from-one-laptop-to-another)

---

### Post by sdowney717 on 2012-10-29
will it work with multiple partitions, grub and windows partitions?

this here "Last step is to install grub on you new disk."
from method 2: Using disk images

So why cant I just make an exact perfect image?
A clone would be a clone and be identical to the original.

---

### Post by sdowney717 on 2012-10-29
[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

how about this method. 
Boot Live CD or Live USB

sudo fdisk –l to find drives
sudo dd if=/dev/sda of=/dev/sdc for whatever sda or sdc is

Will dd erase the drive or should you use gparted to wipe it first?
And perhaps might still need to setup grub, I dont know.

---

### Post by RLDr on 2012-10-29
Use free and open source software for disk imaging and cloning, [**[COLOR="Red"]Clonezilla[/COLOR]**]("http://www.clonezilla.org/") with unicasting and multicasting! [[COLOR="red"]Clonezilla[/COLOR]]("http://www.clonezilla.org/"), based on DRBL, Partclone and udpcast, allows you to do bare metal backup and recovery. Two types of [[COLOR="red"]Clonezilla[/COLOR]]("http://www.clonezilla.org/") are available, [Clonezilla]("http://www.clonezilla.org/") live and [Clonezilla]("http://www.clonezilla.org/") SE (server edition). [Clonezilla]("http://www.clonezilla.org/") live is suitable for single machine backup and restore. While [Clonezilla]("http://www.clonezilla.org/") SE is for massive deployment, it can clone many (40 plus!) computers simultaneously.

---

### Post by oldfred on 2012-10-29
dd is a very powerful command and as such can be dangerous. Just be sure to have command exactly correct as anything else will damage system.

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)
[http://www.anti-forensics.com/disk-wiping-with-dcfldd](http://www.anti-forensics.com/disk-wiping-with-dcfldd)

But you cannot leave both drives connected. They will be identical down to the UUID and trying to boot one may load the other depending on which drive BIOS powers up first.

Of course 5 minutes later you have made changes, so they are not identical.

---

### Post by sdowney717 on 2012-10-29
before your post I am doing this already

> [https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)

Cloning an entire hard disk
From physical disk /dev/sda to physical disk /dev/sdb

dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror

Will I need to reinstall grub?

---

### Post by oldfred on 2012-10-29
Since you are doing entire drive, you should not have to reinstall grub. 

But only test with one drive connected or else you may have issues as you have two identical systems.

---

### Post by sdowney717 on 2012-10-29
dd finished and new drive reboots fine, no need to redo grub
It may have taken less than 30 minutes for dd to finish.
Windows is also there.

> ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
14653926+0 records in
14653926+0 records out
60022480896 bytes (60 GB) copied, 2809.71 s, 21.4 MB/s
ubuntu@ubuntu:~$ 

---

