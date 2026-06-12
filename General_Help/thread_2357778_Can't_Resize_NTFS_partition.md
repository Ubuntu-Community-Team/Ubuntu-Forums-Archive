---
title: "Can't Resize NTFS partition?"
date: 2017-04-06
forum: General Help
---

### Post by tom167 on 2017-04-06
Hello. I am kinda new to ubuntu though I am not new to linux. I am using gparted as my partition editor and I am unable to resize my Windows 10 partition (my NTFS partition) at all. Hibernation is turned off, as I made sure of that, and I have tried solutions to other similar problems to no ado. There is a yellow Triangle next to the partition, and if I right-click and press Information, it says the following:
> Warning:
Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfs-3g / ntfsprogs.
I have tried reinstalling ntfs-3g and ntfsprogs but it doesn't help.
I have tried running ntfsfix and running chkdsk on Windows 10.
I have Ubuntu 16.04.1 (x64) and I have a 2TB Seagate Barracude drive running on SATA.
The Windows partition was fine until today.

Please help. Thank you in advance.

---

### Post by wildmanne39 on 2017-04-06
You want to defrag your windows partitions and resize them from windows, but create partitions for Ubuntu from livecd using gparted.

---

### Post by yancek on 2017-04-06
I would agree with the suggestion above, always resize windows partitions from windows after a defrag and after resizing, you should also run chkdsk from windows.

---

### Post by Bucky Ball on 2017-04-06
> **yancek said:**
> I would agree with the suggestion above, always resize windows partitions from windows after a defrag and after resizing, you should also run chkdsk from windows.


+1, and I'll go one step further: _never_ resize a Windows OS partition with Gparted or any other Linux partition editor. Always use a Windows app. Doing otherwise can cause severe breakage.

I'd also advise three or four defrags or using something more powerful than the default Disk Management tool. PowerDefragger I think was one from the past. That will do a better job.

---

### Post by tom167 on 2017-04-06
Alright. I will defrag and resize from Windows. Thanks you guys for your information and help.

---

