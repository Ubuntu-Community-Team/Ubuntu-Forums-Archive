---
title: "GParted Querstion!"
date: 2007-12-02
forum: General Help
---

### Post by ehdtkqorl123 on 2007-12-02
Hi,

if I run GParted, in the partion list, I have unallocated section which is 2.28GB big.
Also, I have partition sections for Vista and Ubuntu too.
Now, I want to merge that unallocated partition and the ubuntu partition (extended and ext3).
But if I right-click on unallocated partition or extended partition, there is nothing about merging them. In the right-click list, only NEW and INFORMATION these two. 
Can anyone let me know how to merge uncallocated partition and ubuntu partition using GParted?
Thank you!

---

### Post by avik on 2007-12-02
Couldn't you delete the unallocated partition and resize the other partition to fill up the space?

---

### Post by merlinus on 2007-12-02
Are you using gparted live cd?  You cannot resize or add to a partition that is in use (mounted).

---

### Post by ehdtkqorl123 on 2007-12-02
I just downloaded it using

sudo apt-get install gparted

is Gpared live cd the same as ubuntu live cd? 
i dunno what that is...
btw i cannot delete that unallocated partition.. weirdo

---

### Post by ehdtkqorl123 on 2007-12-02
How can I extend the ubuntu partition after I unmount ubuntu partition?
Do I have to use ubuntu live cd and do the partition thing?

---

### Post by merlinus on 2007-12-02
gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by sandysandy on 2007-12-02
> **ehdtkqorl123 said:**
> Hi,

if I run GParted, in the partion list, I have unallocated section which is 2.28GB big.
Also, I have partition sections for Vista and Ubuntu too.
Now, I want to merge that unallocated partition and the ubuntu partition (extended and ext3).
But if I right-click on unallocated partition or extended partition, there is nothing about merging them. In the right-click list, only NEW and INFORMATION these two. 
Can anyone let me know how to merge uncallocated partition and ubuntu partition using GParted?
Thank you!

Hi

you can download the gparted from the link above and burn the ISO image.
after that u can boot from the gparted CD. (Ubuntu live CD also has gparted but mounting / unmounting drives may be required)
after u boot , u will get various options. u can resize partitions with gparted.
a word of advice - its better to backup important stuff before trying out anything new specially resizing etc.

regards

---

### Post by ehdtkqorl123 on 2007-12-02
OMG thanks so much! I wil try right now :0

---

### Post by ehdtkqorl123 on 2007-12-02
Hi I have a quick question.. 
When I run the live CD, which option do I have to choose?
The first one? or which???

---

