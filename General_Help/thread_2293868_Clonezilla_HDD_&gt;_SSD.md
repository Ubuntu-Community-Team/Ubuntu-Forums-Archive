---
title: "Clonezilla HDD &gt; SSD"
date: 2015-09-08
forum: General Help
---

### Post by aaron27 on 2015-09-08
I am having a major issue trying to copy a 300GB HDD to a 120GB SSD. I  have chosen to use Clonezilla as this has never let me down before, I  have used Gparted to resize the larger drive down to just over 100GB.  After thats done I boot into Windows and let ChkDsk do its thing before  then booting back into Clonezilla.  I can confirm that i can see both drives listed for selection and  carefully chose the Source and Target, the first two smaller partitions  copy over fine however on the third and 'main' partition the copy gets  to between 50/70% and then freezes copying.
  I have googled and tried as many of the different options that  Clonezilla offers that I can but all do the exact same thing. We even  tried setting up the partitions on the new drive and doing a partition  to partition clone but same result. To make sure there is no issue with  the SSD we even tried a larger drive but again this did the same thing.
  I dont know how much difference it will make but the machine is a  Dell Latitude laptop, the HDD is a Toshiba 300GB and the SSD is a 120GB  Samsung.
     

Also posted here: [http://serverfault.com/questions/720807/clonezilla-hdd-ssd](http://serverfault.com/questions/720807/clonezilla-hdd-ssd)

---

### Post by Bucky Ball on 2015-09-08
Firstly, never use Linux tools to resize a Win partition. This can cause major damage to the Win partition. So far you have been okay by the looks. Rule of thumb: resize Win with Win software, Linux with Linux.

What are the details of the third partition you are failing on? Bit confused though. You say you have a 100Gb partition you want to clone then say you are cloning three partitions? For clarity:

The partition (target) is how big?
What is the total number of (source) partitions you are wanting to clone and how big are they?

Things to keep in mind. If you are cloning three source partitions you are going to need three target partitions. Period. If you have a 100Gb partition (source) that is only 50Gb full you still need a 100Gb (target) partition to clone to, regardless of the fact the source partition is 100Gb but only half full. From what I've heard, there are other tools that can negotiate this, but Clonezilla, last I used it, isn't one of them. It clones the partition _not_ just the data on it. :)

---

### Post by aaron27 on 2015-09-08
Thank you for your reply.
Yes we have always used it previously and never had an issue (done alot  of HDD > HDD) but will bare that in mind in the future - I guess we  have just been lucky so far.
The overall size of the disk was 300GB, I  have resized it now. sda1-diag-fat16 is 39Mb, sda2-recovery-NTFS is  12GB and sda3-OS-NTFS is 98.18Gb and I then have 187.23Gb of  unallocated.

We have setup the SSD so it has three partitions to the same size ( it was only during googling this issue I found that out).

---

### Post by leunam12 on 2015-09-08
The way I have done this in the past is by doing a disk to disk clone, choosing advanced options as opposed to beginner mode and then choose or check -icds "Skip checking destination disk size before creating partition table". Something else to keep in mind is to make sure that Clonezilla is running live from the USB stick or DVD rather than running from RAM. If you have a dedicated Clonezilla disk this is the default (and I think only option), but if you are running Clonezilla from another distribution such as Parted Magic where the default is to write everything to RAM and run from there, Clonezilla may fail like this because basically you run out of RAM and it simply stops copying.

---

### Post by aaron27 on 2015-09-08
Yes i have checked that option otherwise the copy errors on you.
Thats interesting I am indeed running through Parted Magic, I wonder if that is our issue.

---

### Post by aaron27 on 2015-09-08
Thank you [**[COLOR=#000000]leunam12[/COLOR]**]("http://ubuntuforums.org/member.php?u=1449887")  your advice fixed the issue, went into the live version of clonezilla  and it worked first time. Will make note of that for the future.

---

### Post by Bucky Ball on 2015-09-08
Doh. Yep. Live version. That is it. Never thought you weren't so didn't think of it. :)

Good luck and thanks for marking as solved.

---

