---
title: "/home partition running out of space - increase it with Gparted"
date: 2013-05-12
forum: General Help
---

### Post by cybertronix on 2013-05-12
Hi all

I have over 200GB allocated to Ubuntu but my home partition is only 17GB, I researched this forum how to grow it but I cant figure it out how to do it (see attached pictures for additional information and df -h output at end of this message).

Further, Im not sure if my partition setup is ideal? Im probably missing something / something must be wrong because I cant save anything in (/media)

Any help much appreciated including if I should set up additional partitions and if so where those should be?

Thank you

```

hans@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G   16G  1.1G  94% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           389M  880K  388M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  160K  1.9G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda2       145G  106G   39G  73% /host
/dev/sda1       250G   60M  237G   1% /media/hans/Ubuntu

```

---

### Post by oldfred on 2013-05-13
you have a wubi install which is a folder inside the Windows NTFS partition, not a full partitioned dual boot.
       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Since you already have one ext4 partition, you may want to convert to a full install.
      
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

      
 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

I would be sure to backup your data first. I tend to prefer to install Ubuntu in a 25GB / (root) partition and have a separate /home or data partition(s). If dual booting with Windows then a separate shared NTFS data partition is highly recommended.

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by cybertronix on 2013-05-13
> **oldfred said:**
> 

Since you already have one ext4 partition, you may want to convert to a full install.
      
...

I would be sure to backup your data first. I tend to prefer to install Ubuntu in a 25GB / (root) partition and have a separate /home or data partition(s). If dual booting with Windows then a separate shared NTFS data partition is highly recommended.


Sounds good to me!  

However, Im not sure how to go about creating the new partition (s)....   Should I shrink Sda 1 to 25GB and then creat the new ones out ot what ever is left over?  I would like to share a NTFS partition between Win and Ubuntu  and I am actually going to re-instal windows as it is giving problems

What setup would you suggest ? 

Thank you !

---

### Post by oldfred on 2013-05-13
I might make Windows a little smaller and use a larger NTFS data partition, but you have to decide how large each is. Windows is a lot happier with 30% free space, once it gets to 10% free it really slows down. So leave room. Make the Windows partition sda1, NTFS formatted with the boot flag. You can install Ubuntu all in logical partitions.

My standard suggestions:
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Windows always in hibernation may be an issue.

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by cybertronix on 2013-05-25
Oldfred

Just an update. I did as suggested and created the partitions as per your message, formated and decided to do a clean instal. All seems good now but the common NTFS partition sometimes doesnt show in Ubuntu (but does show in Windows). Apart from that, all is good in the hood! :)

I am going to start a new thread regarding the issue with the common / NTFS partition

Thanks for all your kind help!  

P.S I would like to mark this as solved but I dont understand how to do so :/

---

