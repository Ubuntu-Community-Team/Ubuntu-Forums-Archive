---
title: "Merging partitions"
date: 2012-10-26
forum: General Help
---

### Post by Hsakiv on 2012-10-26
Hi,

Please forgive if the question seems naive.

I had 2 ubuntu versions on my system (11.10 and 12.10) equally distributed over the disk space (250 Gb). 
I uninstalled the version 11.10 using the os-uninstaller. Now I want to use the entire disk space for the version 12.10, but am not sure how to proceed about it. 

I have installed gParted but am not sure what the various file systems mean and which ones to remove. I have important data in the system and unfortunately don't have an external disk right now to take backup.  Hence I want to be really sure about the process.

---

### Post by Bashing-om on 2012-10-26
hi ! too ...

Firstly ..anytime partitions are manipulated there is the chance of data loss and corruption (power outage also happens at the MOST inopportune times) //strongly advised to find a means to back up your important data and files.

GParted on first approach can be a daunting situation ..but in reality is simple and straight forward...be prepared first hand with what you intend to accomplish. There is no forgiving of mistakes !

If the partitions you are deleting are at the first of the disk, real good chance that grub will need to be re-installed (forewarned).

procedure, reduced to oversimplification: delete the partitions, use the graphics arrows to pull the desired partition into the newly created space. The procedure will be less fraught with errors/corruption IF the deleted partitions were on the graphical right
and the expansion of the used partition is thus also to the right into the free space.
Will take some time to grow the partitions to the new size ..lot of data to move ...->patience !

Back up your data !

here is the official howto:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)[INDENT]my best to ya <== BDQ

[/INDENT]

---

### Post by oldfred on 2012-10-26
As Bashing-om says you do need to backup. Use DVDs or flash drive(s) for the most important data. You can always reinstall Ubuntu, but your data is valuable and systems do fail.

You are not showing two ext3 or ext4 Linux partitions. You have a currently mounted ext4 partition, and the extended partition with a NTFS partition and two swaps. The little key symbols show what is mounted or used currently.

You do have to use gparted from a liveCD and even then have to click on swap(s) and swap off to unmount everything. You cannot work on mounted partitions.

Is the nearly empty NTFS partition the one you want to delete?

I see three options. 
One delete NTFS, move extended right to have just swap and merge unallocated that is now outside of extended and adjacent with sda1.
Two is reformat NTFS to ext4 and move /home into that partition
Three is reformat NTFS to ext4 and just use it as a data partition. I have most data normally in /home in my data partition.

You can also delete the sda7 swap as it looks like it is not used.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

---

### Post by Hsakiv on 2012-10-26
Thanks a lot ppl.

Guess I'll take backup first...Till then work in the current setup..

---

### Post by Bashing-om on 2012-10-26
Good ...as there is no real hurry, It is beneficial to do the homework, come up with a dedicated plan for how you want your system for the long term....
the 7 p's apply in this situation ---prior prudent planning prevents -iss poor performance !

the best plans -> include good backup ...then no matter what ..it is fixable (it's ubuntu !)


[INDENT]let us know when we can help <== BDQ
 
[/INDENT]

---

