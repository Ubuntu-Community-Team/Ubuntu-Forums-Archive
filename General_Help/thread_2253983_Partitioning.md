---
title: "Partitioning"
date: 2014-11-24
forum: General Help
---

### Post by cyber-collar on 2014-11-24
Hi all,

Hoping someone can assist with a problem I have. 
I formatted my laptop which I was dual booting Windows 8.1 and Ubuntu 14.04(two partitions). I created a backup of my Ubuntu partition with Clonezilla. After formatting my laptop, I created the following partitions on my 640GB harddrive:
[LIST]
[*]80 GB Windows OS Partition
[*]50 GB Backup Partitions ( To store Ubuntu and Windows backup images)
[*]400 GB Data partition(For my games and other data)
[*]80 GB Linux Partition (For Ubuntu)
[/LIST]

I first installed Windows and created these partitions. Everything was fine. I then booted up in Clonezilla and chose the "restore parts" options. It picked my backup image which I put on my external harddrive. But when I wanted to restore, it only found the first 3 partitions(Win OS, Backup, and Data) and one extra partition that Windows created automatically. It does not pick up the Linux partition. I tried deleting the partition, reformatting with different file systems(NTFS, exFAT) but it does not pick up.

I then downloaded Ubuntu 14.10 and tried to do a fresh install of Ubuntu to that partition but it also does not pick up the partition. I was reading on the Net that you can have 3 or 4 Primary partitions but I don't really understand what that means and if that is my problem?

TIA

---

### Post by Al1000 on 2014-11-24
Hi, the maximum number of primary partitions a hard drive can have is four, so if the four partitions you created are primary partitions and Windows created another one, that will be the problem.

What you ideally want is a maximum of three primary partitions (including the partition that Windows creates), and an extended partition, in which you can create logical partitions.

More information would be required to work out what your best course of action would be at this point:

Do you have anything on the 50GB and 400GB partitions, or is deleting them an option?

Whereabouts on the hard drive did Windows create this other partition, in relation to the partitions that you created?

I take it that you installed Windows on the first partition - is that correct?

---

### Post by cyber-collar on 2014-11-24
Hi Al1000,

Edit: Actually, at first the Linux partition wasn't created. It was just unallocated space. The four partitions were the Win OS, Backup, Data and the one that windows automatically created. I then created the Linux partition from the unallocated space as the 5th partition.

I can delete the "Backup" partition. I have a copy of the backup images on my external. I can also delete the "Data" partition. Windows created this 350Mb partition that it calls system restore partition on Disk management in Windows. And yes, Windows is installed on the first partition. Can I change at this point which partitions are primary and which are extended?

Thanks for the help. Greatly  appreciated.

---

### Post by Al1000 on 2014-11-24
You can create a new extended partition after you delete a primary partition, or two. I would: 

1) delete the "Data" and "Backup" partitions.

2) Then check if the Ubuntu partition shows up, and if it does then delete it as well.

3) If the 350MB partition is not beside the Windows partition, then move it (using an application such as GParted) so that it is. EDIT: If it's at the end of the drive, then I would leave it where it is. I would just move it if it has unallocated space on both sides, so that it doesn't get in the way of the new extended partition.

4) Create an extended partition in the unallocated space, then you can create logical partitions within the extended partition.

What application are you using to create partitions?

---

### Post by cyber-collar on 2014-11-24
I was using the Computer Management(Disk Management) Tool in Administrative Tools. I'll get GParted and try what you suggested. Thanks a lot.

---

### Post by Al1000 on 2014-11-24
Just a further thought: there would be no need to delete the Ubuntu partition if it does show up, so long as you delete the "Data" and "Backup" partitions, if you don't want to have to install Ubuntu again. If the "Data" and "Backup" partitions are next to each other on the drive, then you could just create an extended partition in that space after you delete them.

It would be helpful if you could post a screenshot of your hard drive in GParted, or provide an explanation of what it shows, so that we can see whereabouts the partitions are.

---

### Post by ajgreeny on 2014-11-24
**NEVER** make a partition with Windows that you want to use for Linux. Windows has a habit of making dynamic partitions that Linux can not use, nor even see, if I remember correctly.

You should always shrink a Windows partition with its own utility, and you can delete a partition as well with that, but do not make a new one; just leave it as unallocated space which Linux will then see.

---

### Post by cyber-collar on 2014-11-24
Thanks for the advise ajgreeny.

Cool. I'll update tonight with screenshot.

---

### Post by cyber-collar on 2014-11-25
So I messed up my partitions. :lolflag:
Windows does not start anymore. Have to format again from the start.

---

