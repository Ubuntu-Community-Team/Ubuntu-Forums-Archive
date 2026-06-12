---
title: "Feisty isn't recognizing the partitions on my old HD."
date: 2007-08-09
forum: General Help
---

### Post by Cerebrum on 2007-08-09
Feisty Fawn isn't recognizing the partitions on my old HD.

I already read this thread in another forum, but it didn't help me:

[http://ubuntuforums.org/showthread.php?t=413745&page=2](http://ubuntuforums.org/showthread.php?t=413745&page=2)

My computer has two HDs and Ubuntu is installed on HD-A and is running fine.
I also have a HD-B that I want to read from, but Ubuntu isn't recognizing the partitions.

This HD-B is a Quantum Fireball lct20 with 30 GB of space.
[http://perso.orange.fr/rayp/HD/QUANTUM/guides/fb_lct20.htm](http://perso.orange.fr/rayp/HD/QUANTUM/guides/fb_lct20.htm)

Now here the problems begin. This HD was made to work with old BIOSes, so officialy
it has a CHS of:
16,383 - 16 - 63

It has a "CHS" space of 8.4 GB (16,383 * 16 * 63 * 512 bytes) but of course it is bigger.
But you need a LBA capable BIOS in order to access the whole drive.

Now, in my old computer this was the only HD and I had an old BIOS that only could
access the 8.4 GB so I had to use DDO(Dynamic Drive Overlay) to have access to the full HD. The DDO itself
boots from the HD at the very beginning, but I have no idea how it works.

Ok, this HD-B had the following partitions(the following table is like I would see it from RedHat 8 Linux running
from HD-A):

/dev/hdb1  Windows 98 C: drive
/dev/hdb5  Windows 98 D: drive
/dev/hdb6  Old RedHat Linux installed on HD-B

There was also a Linux Swap partition.
AFAIK, the two windows partitions where logical partitions in one extended partition.

Remember the above refers to the old HD-B.

On HD-A:
Now before I Installed Ubuntu I had an RedHat 8 installed on HD-A and it could recognize the partitions
and read the data from HD-B just fine. I would simply mount the three partitions above and could read all
the data.

Now, in order to be able to read the partitions from Ubuntu I started reading on the forums and people suggested using testdisk to solve it. 

[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Testdisk recognizes the geometry as follows(Note that this differs from the official CHS of 16,383 - 16 - 63):
Disk /dev/sdb - 30 GB / 27 GiB - CHS 3649 255 63, sector size=512

Analysing the HD with testdisk produces the following result:

First it seem to find only the DDO partition:

Disk /dev/sdb - 30 GB / 27 GiB - CHS 3649 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors
 1 * OnTrack DM DDO           0   0 10  3647 254 63   58605111

I cannot change this partition.
After that I click on proceed:

Now the 3 expected partitions appear:

Disk /dev/sdb - 30 GB / 27 GiB - CHS 3649 255 63
     Partition               Start        End    Size in sectors
D FAT32                    0   2  1   244 254 63    3935799 [DISK1_VOL1]
D FAT32 LBA              244   2  1  3284 254 63   48853539 [DISK1_VOL2]
D Linux                 3284   2  1  3629 254 63    5558364 [/]

If I read this correctly the partitions are overlapping.

It recognizes all the relevant partitions but as you can see they all are in "deleted" status, hence the "D" on the far
left column. But I can navigate the files just fine, so the data seems to be OK. Using the arrow keys it is possible to change the status of the partitions but I can only change one partition to primary. If I try to change another partition to a status other than "D" I get a "bad structure" error.
And I cannot make an extended partition.

Now I change the disk geometry to the official CHS 16,383 - 16 - 63 in order to analyse again:

Disk /dev/sdb - 8455 MB / 8063 MiB - CHS 16383 16 63

I get warnings when analysing:

Warning: Incorrect number of heads/cylinder 255 (FAT) != 16 (HD)
  FAT32 LBA                0   2  1  3888  12 63    3919797 [DISK1_VOL1]
Warning: Incorrect number of heads/cylinder 255 (FAT) != 16 (HD)
  FAT32 LBA             3888  14  1 52338  12 63   48837537 [DISK1_VOL2]

After that I go to the following screen:

Disk /dev/sdb - 8455 MB / 8063 MiB - CHS 16383 16 63
     Partition               Start        End    Size in sectors
L FAT32 LBA                0   2  1  3888  15 63    3919986 [DISK1_VOL1]FAT32, 2007 MB / 1914 MiB

And then:

Disk /dev/sdb - 8455 MB / 8063 MiB - CHS 16383 16 63

     Partition                  Start        End    Size in sectors
 1 E extended LBA             0   1  1  3888  15 63    3920049
 5 L FAT32 LBA                0   2  1  3888  15 63    3919986 [DISK1_VOL1]

So suddenly he recognizes an extended partition and a logical one.

Any suggestions of how I solve this mess?

Thanks a lot!

---

### Post by notatoad on 2007-08-09
can you see the partitions in GPartEd?  first thing i do when a partition doesn't work for me is to look in GPartEd and see if it can tell me what's wrong

edit:  read your post again and realized you know what you're doing way more than i do, and can probably already see everything that gparted could tell you.

---

