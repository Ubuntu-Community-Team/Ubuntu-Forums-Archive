---
title: "can't wipe out a disk"
date: 2018-02-09
forum: General Help
---

### Post by danielsender on 2018-02-09
I was running 16.04.3 on a 32b machine with a new disk. Something went wrong so I wanted to re-install the system, but it kept failing. So I decided to completely wipe out the HD by doing 'dd if=/dev/zero of=/dev/sdc" from the live CD, and after only 1GB the copying stops saying "No space on device", when in reality the disk is a 320gb. Is there another layer of information on the HD that I have to edit to bring that to sanity?

---

### Post by deadflowr on 2018-02-09
What does something like 
```
sudo parted -l
```
tell you?

---

### Post by HermanAB on 2018-02-09
Are you sure that you are writing to the correct disk?  Chances are that you deleted something else...

---

### Post by danielsender on 2018-02-09
> **HermanAB said:**
> Are you sure that you are writing to the correct disk?  Chances are that you deleted something else...

Yes, it is the right HD. I will run the 'parted -l' tonight when I get home. I ran 'sudo fdisk -l' and it listed all the disks on my system. /dev/sdc is connected with an USB adapter. I also ran (from the live CD) gparted. /dev/sdc is shown all in gray with a sign saying "unallocated" or something like that.

---

