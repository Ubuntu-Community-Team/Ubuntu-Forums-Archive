---
title: "No were to put receipt for new hard drive."
date: 2007-06-11
forum: General Help
---

### Post by damota on 2007-06-11
How do I get Ubunto to use a second hard drive I have just fitted instead of it telling me I can not write to it or change it's permisions because I do not own the hard drive that I put in.
If I reload the computer from scratch will it then find the hard drive when loading and realize it is part of the system, or will I still have this problem.

Dave

---

### Post by odiseo77 on 2007-06-11
Ubuntu should see the new HD as long as you have it properly configured (eg. as slave, master, etc (if it's a 2nd HD, then it should be as slave). Maybe it just doesn't seem to see it because it doesn't have partitions in it? What's the output of **sudo fdisk -l** ?? In case it's already partitioned, have you created mount point(s) for the partition(s) you want to use? Please note that you must create the mount point(s) in /media or /mnt as root; you can do it by typing **sudo mkdir /media/myhd** (you can change "myhd" for the name you want, of course). After you've created the mount point, mount the partition by typing **sudo mount /dev/partition_device /media/myhd** where "partition device" is the name the partition has in /dev (for example /dev/hdb, /dev/hdc /dev/sdb, etc; depending on your configuration and your drive).

Regards.

---

### Post by damota on 2007-06-11
It sees the hard drive and can read from it but I can not write to it. If I try to change the permissions to let it read and write Ubuntu say as it is ?not my hard drive? I am not allowed. I have it formated in NTFS so it can swap stuff to and from  XP when I change the OS system caddy over. It will not allow me to reformat the drive either.
I have separate OS,s on different HD caddies and the hard drive that is fitted in my computer (the one Ubuntu won't write to) stores files to be used by the other drives when slid into the computer.

Dave

---

### Post by cward002 on 2007-06-11
Hi Dave.

In order to be able to write to NTFS drives under Linux you have to install a special driver that enables write support. The driver is called ntfs-3g. I am not sure if it is available in the repos. Another option is to format the drive as FAT32 which can be read and written to natively in both Linux and Windows. If you have any questions about nything feel free to post back and I will try to help.

Colin

---

### Post by danhm on 2007-06-11
There are also tools that let Windows read/write to [ext2/ext3](http://www.fs-driver.org/) (although the ext3 write support seems to be a little patchy at best) or [reiserfs](http://rfsd.sourceforge.net/) (I don't know anything about this one).

---

### Post by damota on 2007-06-11
Thank you, I took Colin's second option and formated the drive to fat 32. The drive shows in Media and when I click on it it allows me to read and write to it now after I put in my password.
There is nothing on my computer that needs a password so is there a way to get rid of having to do that?
As you may have guessed this is the first Linux I have really liked, it is the Ubuntu Studio I am using mainly but I also have Kubuntu (both have different things I like) as well as XP on caddies that I just swap over. 
If I am stuck with having to put the password in, there is no need to reply. I am happy as it is, that would just be the icing on the cake (so to speak).
Again thank you all.

Dave

---

### Post by odiseo77 on 2007-06-11
If you want to give your user read and write permissions to your fat32 partition, simply umount it, add an entry similar to the following to your /etc/fstab:

```
/dev/YOUR_PARTITION    /media/MOUNT_POINT     vfat      defaults,auto,utf8,uid=your_username,gid=your_username,umask=007  0          0
```

After you've added this entry to your /etc/fstab mount it with **mount /media/MOUNT_POINT** and your user should have read-write access to it (besides, after every reboot you'll have your partition mounted automatically).

Regards.

---

### Post by Jose Catre-Vandis on 2007-06-11
You will probably need to create a mount point in your media directory:

In a terminal
```
sudo mkdir /media/MOUNT_POINT
```
(using your preferred name for MOUNT_POINT)
then run the 
```
sudo mount -a
```
command to remount all your mounts, including the new drive


> **odiseo77 said:**
> If you want to give your user read and write permissions to your fat32 partition, simply umount it, add an entry similar to the following to your /etc/fstab:

```
/dev/YOUR_PARTITION    /media/MOUNT_POINT     vfat      defaults,auto,utf8,uid=your_username,gid=your_username,umask=007  0          0
```

After you've added this entry to your /etc/fstab mount it with **mount /media/MOUNT_POINT** and your user should have read-write access to it (besides, after every reboot you'll have your partition mounted automatically).

Regards.

---

