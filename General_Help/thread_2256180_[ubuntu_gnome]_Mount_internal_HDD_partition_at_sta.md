---
title: "[ubuntu gnome] Mount internal HDD partition at startup?"
date: 2014-12-10
forum: General Help
---

### Post by KillEmAllx on 2014-12-10
Hi guys,
I'm wondering if there is any way to automount an internal HDD partition?
I have Ubuntu Gnome 14.04 installed on a SSD, and a 1TB HDD divided in half, one NTFS-partition for a Windows 7 installation, and one ext3/ext4-partition named 'Linux HDD'. Both partition show in Nautilus, and I can access them both without any problems.
What I want to do is to mount the Linux HDD at startup instead of having to manually mount it everytime I use applications that make use of the drive, like Steam and VirtualBox.
I have tested to disable "automatic mount options" with the Disks application and manually select "mount at startup" and "show in user interface", but it gives me an error when booting saying something like "can't mount drive, press S to continue".
Any ideas?
Thanks in advance.

---

### Post by Bashing-om on 2014-12-10
KillEmAllx; Hello;

> 
I'm wondering if there is any way to automount an internal HDD partition?

That is done with an addition to the ' /etc/fstab' file.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <-bodhi.zazen-Understanding fstab

My bit to try and help

[INDENT][INDENT]ain't noting but a thing
[/INDENT][/INDENT]

---

### Post by KillEmAllx on 2014-12-14
I did it! I edited the fstab file using the answer in this post: [http://askubuntu.com/questions/481898/cant-automatically-mount-ext4-partitions-under-ubuntu-14-04-but-can-mount-ntfs](http://askubuntu.com/questions/481898/cant-automatically-mount-ext4-partitions-under-ubuntu-14-04-but-can-mount-ntfs)
Thank you for the help!
This thread is now solved.

---

### Post by Bashing-om on 2014-12-14
KillEmAllx; Outstanding !

You do good work, Thanks for sharing your solution.

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

