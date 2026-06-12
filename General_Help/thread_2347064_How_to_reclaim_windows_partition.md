---
title: "How to reclaim windows partition"
date: 2016-12-21
forum: General Help
---

### Post by Karl_Ritson on 2016-12-21
I decided to make the switch to Linux with the purchase of a new laptop. Stupidly, I thought I would at some point want to use windows again so I divided the hard drive into 2 main partitions - one for Ubuntu and one for Windows. This was a mistake. Now I've been happily using Ubuntu for over 12 months and not once needed to go back to Windows. So I'd like to reclaim the space that windows is taking up on my hard drive and have a pure Linux machine.

I'm using 64-bit Ubuntu 16.04 LTS I have 8 GB of RAM and 350 GB hard drive. The processor is AMD A10-5750M APU.

Any help appreciated and thanks for your time,
~K

---

### Post by btindie on 2016-12-21
It depends on how you've installed your system. Are you just using a MSDOS / GPT partition table or LVM?

And generally under Linux you'd have multiple partitions or lv's for different directories of the OS such as /home. This is so if you fill up /home it won't affect the root '/' partition.

In it's most basic form you can simply create a LiveCD/USB of [http://gparted.org/](http://gparted.org/) and boot into that. Delete the windows partition then first move your ext4 partition and finally resize it. If you've got anything important on there it may be wise to first back it up.

---

### Post by yancek on 2016-12-21
Posting the output of 'sudo fdsik -l' would provide us with some details.  If you simply have two partitions, one for Ubuntu and the other for your windows and want to use the windows partition in Ubuntu, simply format the windows partition with a Linux filesystem type, create a mount point for it and an entry in /etc.fstab.

---

