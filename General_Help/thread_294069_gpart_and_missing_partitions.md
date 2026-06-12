---
title: "gpart and missing partitions"
date: 2006-11-06
forum: General Help
---

### Post by Stochastic on 2006-11-06
Hi, I had some partitions disappear on me while reinstalling and I'm trying to sort things out.  So far I've gotten all but one partition back but I'll outline things to get you up to speed.

My 80gig (actual 74gig) used to be partitioned as such:
25gig (or so) partition that housed Ubuntu (ext3)
2gig backup of /home (ext3)
46gig data partition (fat16) - I used to share this with a windows partition hence the fat16 partition
1gig swap

Ubuntu crashed during the first reinstall (I was reinstalling after edgy upgrades messed up my system) but upon subsequent reinstalls the 46 gig and the 1gig swap was not recognised by any installer (suse, debian, gentoo, ubuntu, etc..).  To make things worse, my CDrom motor died on me while I was running all these live CDs but warranty has one in the mail to replace it already.  I reinstalled ubuntu (network install) with the following partition table:

12gig ext3 -ubuntu
1gig swap
12gig free space (left so that I could do system testing/backups etc)
2gig /home ext3
47gig "free space"/missing partitions

Using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") I was able to get the computer to recognize both the 46gig and the original 1gig swap, however upon reboot, I got a Grub Error 17.  So upon another network install ubuntu's installer told me I had:

27gig free space
46gig fat16
1gig swap

So I installed Ubuntu and am currently running with the following partitions:

10gig ext3 -ubuntu     -hda2
17gig free space
46gig fat16            -hda1
1gig swap              -hda5

I want to recover the data that was on my 2gig /home partition and then I'm back to being a happy man. (there's more mucking around I'd like to do later but that's all I need to do for now).  

When I run gpart it sees the following:

10gig ext3         -primary partition 1
2gig free space
1gig swap          -primary partition 2
12gig free space
2gig ext3          -primary partition 3
46gig fat16        -primary partition 4
1gig swap          -5th primary partition (invalid)

Since I've gotten this far, I need some advice before I muck further and loose my 46gig again.  Should I tell gpart to write this partition scheme to disk? ```
sudo gpart -W /dev/hda /dev/hda
``` and if I do that, will my partition numbers be messed up so I have to rewrite/edit /etc/fstab before reboot?  Are there any other tools to try or suggestions?  Please guys would really like any help available and can't find much documentation on gpart.

---

### Post by Sef on 2006-11-06
To get the data off your 2 GB home partition, download [Knoppix]("http://knoppix.org"), then put it in the cd-rom drive.  Before booting the system, put a usb key in a usb port.  Knoppix should recognize both your hard drive and your usb key.  Transfer the files from your hard drive to your usb key.  Note:  Since GParted is picking up the partition as free space, you may have lost some or all of your documents.

---

### Post by Stochastic on 2006-11-06
> **Sef said:**
> To get the data off your 2 GB home partition, download [Knoppix]("http://knoppix.org"), then put it in the cd-rom drive.

But my CDrom drive is broken, I can wait the two weeks for the replacement drive to show up if you truly believe writing the gpart partition might screw things up.

Also, the largest USB key I own is 512mb, so it's nearly useless as a storage place for my data.

---

### Post by Stochastic on 2006-11-06
anyone else have any input?

---

