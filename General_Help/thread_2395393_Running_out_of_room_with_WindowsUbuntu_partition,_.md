---
title: "Running out of room with Windows/Ubuntu partition, not sure what to do"
date: 2018-07-01
forum: General Help
---

### Post by carykh on 2018-07-01
Hello! Right now I have this drive with about 1 TB of space that started as 100% Windows 10. About a year ago, I didn't have any experience with partitioning drives, but I wanted to add an Ubuntu partition, so my brother offered to do it for me. He set up a 20 GB Ubuntu 16.04 partition, which is the rightmost one in the image. Well, this one started to fill up real fast, so as it filled up, I'd move files to external drives as best I could. We also created a new partition called "doiblio" that's between the Windows and Ubuntu partitions, for some extra space.

Now, the /usr, /home, and /lib folders alone are taking up most of the 20 Gb. I know it is possible to move those to other partitions / connect them with symbolic links. However, that seems kind of risky, and might just be delaying the inevitable filling up again.

In a case like this, is there an easy way to re-partition my drive to give the original Ubuntu partition more space? If I do that, I know I should backup what's in the Ubuntu partition, but should I also backup the 400 Gb of stuff in the Windows partition, too? Or is it safer to just link files to the doiblio drive? Thanks so much!

[IMG]https://i.imgur.com/YdWkIiF.png[/IMG]

---

### Post by yancek on 2018-07-01
Your Ubuntu filesystem partition (sda5) is almost full but your data partition on sda4 has 65GB available.  Use sda4 for data, copy your pictures, music, documents and any non-system files there.  You could also shrink the sda2 windows partition and create a new data partition there to be shared by Ubuntu and windows.  You you also shrink that windows partition and move sda4 to the left but that involves moving data and poses a greater risk of data loss.  Before doing anything, make sure you have important data backed up.

---

### Post by TheFu on 2018-07-01
There is no easy solution with your current setup. Sorry.   There are lots of solutions, but due to using MBR partitioning, there are limitations.  
I would buy a new HDD and layout everything the way I wanted at the start, then move things over. slowly.
* use GPT if you can; it doesn't use "extended partitions" and has no practical limit on the number of primary partitions.  Linux works with both MBR and GPT, but you'll need to research any Windows limitations.
* setup Windows with the amount of storage it needs; I'd split the OS and Data into 2 separate partitions.
* For Linux, I'd reinstall using LVM, using PVs, VGs and LVs to get to:
** / - 25G
** swap - 4.1G (assuming you don't hibernate)
** /var/  - whatever makes sense to your needs
** /home/ - whatever is left

LVM needs 1 partition.  LVs are like partitions, without the limitations. They can be resized up and down if you use ext4. Other file systems can be resized up only.  With LVM, it is a good practice NOT to use all the available storage for all LVs, but to leave a bunch unused to help scaling up later. LVM is very flexible.  Bad thing about LVM is that it is more complicated.

To use LVM in a dual boot setup, you have to do everything manually on the storage assignments. Unfortunately, Ubuntu's storage setup isn't the most intuitive.

The

---

