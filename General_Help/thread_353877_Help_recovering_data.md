---
title: "Help recovering data"
date: 2007-02-05
forum: General Help
---

### Post by thekidder on 2007-02-05
I have 4 partitions on my laptop. One is a swap partition, two others contain Edgy and Feisty, and the last is my /home partition. All of the partitions are ext3. Normally I use Edgy, but I sometimes boot into Feisty to see how it is progressing. Sometime last night when I started up my computer I found around half the files in my /home partition gone. I first noticed this when my desktop had reverted back to its original Ubuntu look and my settings were gone. The partition mounted fine, fsck gave no errors, half the files were simply gone. Some of the missing files I don't miss that much, but others (mostly code) I would really like to recover. 
I don't know when the files disappeared, but what I think happened was this:
I was in Edgy, and I decided to disable my swap partition, on account of receiving new RAM to make 2GB total. I read something that had me edit /etc/sysctl.conf and change vm.swappiness to 0. Some time later, I tried to hibernate the computer, to see if anything had changed since I last tried it (I use the fglrx drivers and hibernate/suspend has never worked reliably). The screen went black but the computer didn't turn off, so I forcibly powered it off by holding down the power switch. I think this is where the data loss may have occurred, but I'm no expert and this is just a guess. After I had discovered that I had lost data, I made sure the partition was unmounted, and it has only been mounted since in read only mode, but there may have been some data written to it before I noticed.

Is there any way to recover these files? As I said, most of the important files were plain text, mostly php and C++ code. I would be happy if those were the only things I could get back.

---

### Post by aysiu on 2007-02-06
I have no idea, but maybe [this thread](http://ubuntuforums.org/showthread.php?t=316271&highlight=recover+deleted+files) might help you.

---

