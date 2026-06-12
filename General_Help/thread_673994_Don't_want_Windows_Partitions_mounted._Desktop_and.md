---
title: "Don't want Windows Partitions mounted. Desktop and Nautilus"
date: 2008-01-21
forum: General Help
---

### Post by jetsurgeon on 2008-01-21
Hello,

Been using Ubuntu 7.10 for a week now, I really like it so far, and this is coming from a really really long time Windows user....... Imagine that!  :)  Actually I like it so much, if I can figure out some of this stuff, the wife and I will be dumping "Windows" for good.....  yea yea ...

Anyway I've got this little problem, and I'm looking for some help and a solution.

**Background:** I have one hard drive in this laptop (100GB) which I have partitioned off into many different partitions, Installed Windows XP and Ubuntu 7.10.

**Problem:**    When I'm in Ubuntu, the partition which holds** Windows XP** and the other partition which holds the **Windows XP Paging file**, are automatically mounted and visible within Ubuntu.  Both partitions have "DRIVE ICONS" on the desktop and when I'm in "Nautilus", both drives show up in the left hand column.   
[B]
What I'm looking for is:[/B] A solution to make both of these partitions to **NOT SHOW UP** from within Ubuntu, on the "Desktop" and within "Nautilus".  Basically I don't want to access them from the Ubuntu side of things or even be visible. 
[U]
**sda1** (Windows XP)  and **sda2**  (Windows XP Paging File)  are the two partitions I'm talking about.[/U]

Can this be done, and if so can you please help me out?

Here is my fdisk -l output:

```

jgadmin@notebook:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19c019c0

   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        4085     2096482+   7  HPFS/NTFS
/dev/sda3            4086        5301     9767520   83  Linux
/dev/sda4            5302       12161    55102950    5  Extended
/dev/sda5            5302        5544     1951866   82  Linux swap / Solaris
/dev/sda6            5545        6152     4883728+  83  Linux
/dev/sda7            6153        6760     4883728+  83  Linux
/dev/sda8            6761        9799    24410736   83  Linux
/dev/sda9            9800       12161    18972733+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x583e7d94

   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1        4016    32258488+   c  W95 FAT32 (LBA)


```

Here is the output of the fstab file:

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f7a77ad1-27d1-463f-b4ef-5f2c92c4f75d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=4b10a28c-c460-48e4-815e-e33883a246e6 /home           ext3    defaults        0       2
# /dev/sda1
UUID=469468ED9468E0C3 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=36B00B7AB00B403B /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=16bab60d-9018-46a7-922c-fb2302217185 /tmp            ext3    defaults        0       2
# /dev/sda7
UUID=ec633b03-6c9c-43a0-ab17-0e3c6d44dad2 /var            ext3    defaults        0       2
# /dev/sda9
UUID=1431-5C80  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=8cf72302-0ae5-44ae-8bae-13be8149460c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Thank you so much for your time and attention in resolving this problem.

All the best,
Jeff

---

### Post by wieman01 on 2008-01-21
Just comment these 2 lines and both partitions should magically 'disappear' (there is actually less magic to it than one might think):
> # /dev/sda1
[COLOR="Red"]**#**[/COLOR]UUID=469468ED9468E0C3 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

# /dev/sda2
[COLOR="Red"]**#**[/COLOR]UUID=36B00B7AB00B403B /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
That's it. Now restart the PC and you should not see any partition icons on the Desktop.

---

### Post by jetsurgeon on 2008-01-21
Ok I did comment out the two lines you mentioned, and yes the Drive Icons do not appear on the desktop.  Yea!    

But thats only one half of the problem.

How do I make them two partitions NOT show up from with in Nautilus?

Thx,
Jeff

---

### Post by wieman01 on 2008-01-21
> **jetsurgeon said:**
> Ok I did comment out the two lines you mentioned, and yes the Drive Icons do not appear on the desktop.  Yea!    

But thats only one half of the problem.

How do I make them two partitions NOT show up from with in Nautilus?

Thx,
Jeff
Just delete the bookmarks? I don't use Nautilus, but I think these icons are just bookmarks/links that you could simply delete. Nothing serious as the partitions aren't mounted anyway.

---

