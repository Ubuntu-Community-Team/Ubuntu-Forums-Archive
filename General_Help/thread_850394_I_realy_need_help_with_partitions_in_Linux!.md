---
title: "I realy need help with partitions in Linux!"
date: 2008-07-05
forum: General Help
---

### Post by ipowerboy93 on 2008-07-05
I installed Ubuntu Linux 8.04, 30 minutes ago, and i have some realy important problems:

So..

- I installed Ubuntu on the partition where i had installed Window, but when i was using Windows i had 2 partitions, C:\, and D:\, i formated and installed Ubuntu on C:\, and i keep files in D:\, now, in Ubuntu, when i'll try to open D:\ (now named "New Volume") i get error message : "cannot mount volume".
I have realy important files, documents, pictures, and other files on that partition.

I need help realy!

Than you!

---

### Post by unutbu on 2008-07-05
**If your partition is an NTFS partition** then
open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)). Type ```

sudo apt-get install ntfsprogs ntfs-config
gksudo ntfs-config

```
Use the ntfs-config program to enable write support.

Now create a mount point for the partition:
```
sudo mkdir /media/Windows
```

You should now be able to mount your partition (using Nautilus) or by typing the command

```
sudo mount /dev/sda2 /media/Windows
```
where /dev/sda2 should be changed to the name of your Windows partition. (See below if you are unsure what the device name of your partition is.)

-------------------------------------------------
**If your partition is FAT16 or FAT32**, then type
```
sudo fdisk -l
```
(The last letter is a lower case L, not a one).

Included in the output should be something like this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         660     5245222+   b  W95 FAT32
/dev/sda3   *         661       38536   304238970   83  Linux
/dev/sda4           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris
```

In Linux the partitions have names like /dev/sda1 rather than drive letters like C:.
Find the Linux name for the partition you wish to mount. Suppose the partition is /dev/sda2 (In my example above, /dev/sda2 is a FAT32 partition).

Now create a mount point of the partition:
```
sudo mkdir /media/Windows
```

Armed with the name of the partition, you are now ready to edit /etc/fstab:

```
gksu gedit /etc/fstab
```

The file will look something like this:```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=33b7e11e-5bdb-4e98-b626-671b1c4d18eb none swap sw 0 0
/dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec 0       0
```

Add this line to the bottom of the file (changing /dev/sda2 to the proper name for your partition):
```

/dev/sda2 /media/Windows vfat  utf8,uid=1000,gid=1000,umask=002 0 0

```
Save the file and Quit gedit. This will give the primary user full read and write  permissions, and read-only permissions for others.

You should now be able to mount your partition (using Nautilus) or by typing the command

```
sudo mount /dev/sda2 /media/Windows
```

(Again, change /dev/sda2 to the proper name for your partition.)

---

### Post by cariboo on 2008-07-05
Could you open up a terminal (Application-->Accessories-->Terminal) and type:

```
sudo fdisk -l
```

And paste it in your next post, this command will show us what your partitions are.

To paste the output just highlight the output and then in your post just click the wheel if you have a wheel mouse or click the right and left mouse buttons at the same time if you have a two button mouse.

Jim

---

### Post by HotCupOfJava on 2008-07-05
I hate to say this, but if the D: partition you are referring to was using the Windows NTFS or FAT32 filesystem you may have trouble retrieving the info through the linux OS.....it uses a different filesystem.

---

### Post by HotCupOfJava on 2008-07-05
This may seem complicated, but you might be able to get your info back this way: Load the live Ubuntu CD again, and go to SYSTEM>ADMINISTRATION>and open the program labeled "partition editor". This will show you what partitions you have on your disk. You can then resize or remove any of the partitions. You can resize them to create empty (no filesystem) space on the disk again, then reinstall Windows on the empty space. You should then be able to boot into Windows and retrieve your info. Then, you must use the live CD to run the same partition editor again to create FREE space for Ubuntu again. Don't rely on the partition editor (Ubiquity) that the installer uses. It will not work well with multiple partitions already installed. When you DO reinstall, select "guided, use the largest contiguous free space". This will install Ubuntu in the FREE space you created with the partition editor while you were running the live cd.

Hope this helps. Good luck.

---

### Post by bodhi.zazen on 2008-07-05
> **HotCupOfJava said:**
> I hate to say this, but if the D: partition you are referring to was using the Windows NTFS or FAT32 filesystem you may have trouble retrieving the info through the linux OS.....it uses a different filesystem.


Umm .... That is simply not true. Linux will handle FAT and NTFS partitions without any problem.

> **ipowerboy93 said:**
> I installed Ubuntu Linux 8.04, 30 minutes ago, and i have some realy important problems:

So..

- I installed Ubuntu on the partition where i had installed Window, but when i was using Windows i had 2 partitions, C:\, and D:\, i formated and installed Ubuntu on C:\, and i keep files in D:\, now, in Ubuntu, when i'll try to open D:\ (now named "New Volume") i get error message : "cannot mount volume".
I have realy important files, documents, pictures, and other files on that partition.

I need help realy!

Than you!

Well, first Linux uses different terminology to refer to partitions (C:\ and D:\ are not helpful).

See : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

Now to mount your partitions, well need to first list them. Please post the output of these commands (you can copy and paste from the terminal) :

```
sudo fdisk -l

mount

cat /etc/fstab
```

---

### Post by ipowerboy93 on 2008-07-06
Thanks, guys, but, when i enter any command in the terminal, the terminal, is asking me for password, and when  i'll try to enter the password, simply noting is written. I am typing on my keyboard but place is blank. The same like, you are trying to write something but your keyboard is not connected to computer.
My is connected and works fine in other text editors, even in the terminal, when he is not asking me for pass.

Please.

---

### Post by Elfy on 2008-07-06
That is normal - put your password in, make sure spelling and case are correct and enter.

---

### Post by Habbit on 2008-07-06
I had long thought that Ubuntu needs some kind of fstab manager... And I have a free summer :KS I'm not formally announcing the start of a project, but how difficult is it to build PyGtk apps?

---

### Post by ipowerboy93 on 2008-07-06
> **unutbu said:**
> **If your partition is an NTFS partition** then
open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)). Type ```

sudo apt-get install ntfsprogs ntfs-config
gksudo ntfs-config

```
Use the ntfs-config program to enable write support.

Now create a mount point for the partition:
```
sudo mkdir /media/Windows
```

You should now be able to mount your partition (using Nautilus) or by typing the command

```
sudo mount /dev/sda2 /media/Windows
```
where /dev/sda2 should be changed to the name of your Windows partition. (See below if you are unsure what the device name of your partition is.)

-------------------------------------------------
**If your partition is FAT16 or FAT32**, then type
```
sudo fdisk -l
```
(The last letter is a lower case L, not a one).

Included in the output should be something like this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8         660     5245222+   b  W95 FAT32
/dev/sda3   *         661       38536   304238970   83  Linux
/dev/sda4           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris
```

In Linux the partitions have names like /dev/sda1 rather than drive letters like C:.
Find the Linux name for the partition you wish to mount. Suppose the partition is /dev/sda2 (In my example above, /dev/sda2 is a FAT32 partition).

Now create a mount point of the partition:
```
sudo mkdir /media/Windows
```

Armed with the name of the partition, you are now ready to edit /etc/fstab:

```
gksu gedit /etc/fstab
```

The file will look something like this:```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=33b7e11e-5bdb-4e98-b626-671b1c4d18eb none swap sw 0 0
/dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec 0       0
```

Add this line to the bottom of the file (changing /dev/sda2 to the proper name for your partition):
```

/dev/sda2 /media/Windows vfat  utf8,uid=1000,gid=1000,umask=002 0 0

```
Save the file and Quit gedit. This will give the primary user full read and write  permissions, and read-only permissions for others.

You should now be able to mount your partition (using Nautilus) or by typing the command

```
sudo mount /dev/sda2 /media/Windows
```

(Again, change /dev/sda2 to the proper name for your partition.)
This Worked! :>
Thank You!

Now I'm proud user of Ubuntu Linux, instead of Windows. :)

---

