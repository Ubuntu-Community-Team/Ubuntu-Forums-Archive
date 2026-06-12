---
title: "Computer's hard drive configuration"
date: 2007-07-28
forum: General Help
---

### Post by that guy on 2007-07-28
I need some advice on the best way to solve a problem.  Thanks in advance.

I have an old desktop that I'm looking to get setup into a file/music/print server.  I have 2 160GB hard drives and 1 20GB.  I want to put the OS on the 20GB and use the rest for storage.  I have >160GB of music.  mt-daapd (music server app) only lets you serve from one folder, so what is the best way to get music from two drives to appear as if it's in the same folder?

Is it possible to mount two drives from the same location?  

I have done some reading about creating a RAID array out of the two 160 drives, but that seems like a lot of work for such a simple thing.

Thanks for any advice anybody has.

---

### Post by Happy_Man on 2007-07-28
Hmmm.... well....

Install Ubuntu to the 20 GB, having that drive as Master. Then, mount one of the big drives, and see whether you can mount the other drive in a folder in the first drive. That's about as good as I've got.

---

### Post by ddrichardson on 2007-07-28
[This]("http://www.howtoforge.com/linux_software_raid") might be worth a look.

---

### Post by that guy on 2007-07-28
Thanks for the help.

I found out that you can easily set up a RAID during installation.  I installed a command-line system from the 7.04 alternate CD.  I'm not sure if the RAID configuration option is available on the other CDs.

How I did it:

When you get to the partitioner select the Manual option.

Delete all of the partitions that you do not want to save (ie. a windows install)

I installed the OS on a disk all its own so I created partitions as you normally would on the primary drive.

For the secondary drives (the ones that will make up the RAID) create partitions for whatever your purpose.  In my case: sdb - 158GB + 2GB  and sdc - 158GB + 2GB 
So now there are two partitions (one for data and one for swap) on each of the two disks (they need to be identical size).  Under "Use as" select "physical volume for RAID"  You will define mount points later.

After the partitions are created select "Configure Software RAID" > Create MD device

Match the two partitions for data and select Finish, then Create MD device and match the next two partitions.  Do this for each of the partitions in the RAID.

After this step is finished, you will see the MDs in the list of disks and partitions.  At this point select the various mount points that you want or set the to swap.

Write the changes to the disks and continue normally with the installation

Yes, it's that easy.

---

