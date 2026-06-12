---
title: "Placing /home In A New Partition, And Viewing It From Windows?"
date: 2013-06-14
forum: General Help
---

### Post by RocketPenguin on 2013-06-14
Hello Ubuntuforums! I have yet another question for you. I recently installed Windows (Turns out i need it for a few things not yet supported my Ubuntu) and i would like to be able to view all my data from both OSes. Now, i would like to mount /home in a third partition, in case one OS or the other fails, making it easy to recover. I would also like to be able to view this /home directory/partition/whatever its called from Windows, that being the way my data is universal. Now, i hear there is an issue on WIndows reading the sort of partition that ubuntu needs in order to mount /home. Any way that I could make it work? I really don't want to have to stick anything i want to see on Windows into another file that is located on the third partition... Rather Have ALL my files located there, and whenever anything is saved, it is saved to /home/the third partition.

---

### Post by oldfred on 2013-06-14
You must keep a separate /home as Linux formatted and any of the Windows drivers to read (only) of Linux partitions may work, but are not really suggested.

Better just to use another NTFS data partition. I keep /home inside my / (root) and have two data partitions, one NTFS and the other Linux. I still have NTFS even thought I stopped booting XP a year ago, but all new data goes into my Linux fromatted data partition.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

    
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

---

### Post by RocketPenguin on 2013-06-15
So basically, what your saying is, don't do it?

---

### Post by ahallubuntu on 2013-06-15
~

---

### Post by Sef on 2013-06-15
> [COLOR=#000000]Better just to use another NTFS data partition.[/COLOR]

+1. Both Linux and windows can read/write to it.

---

### Post by zero2xiii on 2013-06-15
Hay,

I might be completely off to what to wish to accomplish, however have a look here for possible solutions:
[http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)
[http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

Cheers

---

