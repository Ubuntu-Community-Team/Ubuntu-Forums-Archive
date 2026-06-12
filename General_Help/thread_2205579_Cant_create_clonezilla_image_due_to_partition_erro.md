---
title: "Cant create clonezilla image due to partition error message"
date: 2014-02-14
forum: General Help
---

### Post by pretty_whistle on 2014-02-14
I have Ubuntu 13.10.

I've been getting this error message since I put Ubuntu into a new laptop last year using a saved disk image I restored with clonezilla.  It's been running fine but when I went to make a new disk image with clonezilla I got this:
The clonezilla error claims my partitions are overlapping.  

I'm thinking it's an error I should ignore because everything's been running perfectly so how can they be overlapping?!

What do you think?  Should I just ignore this error?

---

### Post by pretty_whistle on 2014-02-14
2nd question:

Can I use Ubuntu "disks" utility to create and restore an image instead of using clonezilla?  I would think so...

What do you think?

---

### Post by coldcritter64 on 2014-02-14
Have you tried fdisk to check and see if any notes about partitioning problems show up ? 
Try ```
sudo fdisk -l
``` that is a lower case L, the command may confirm or show up any discrepancies.
Testdisk (available in the repositories) could also be used to check for problems.

re 2nd question: Check the partitions for problems 1st, however I personally use dd in the terminal to create data dump snapshots of partitions or full drives into ".img" image files. The beauty of such files is the image can be loop mounted and accessed (if mounted read only) or written to (if mounted as re-writeable). Compression of the images is possible by piping output to gzip etc (I have plenty of HDD space,  so don't need to compress my images).

I don't use the disks utility, but as far as I understand it, it is more for creating partitions, I don't think it creates images (though could be wrong on that).

---

### Post by pretty_whistle on 2014-02-14
Pasting in sudo fdisk -l gave me this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b6f69


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      688128   956338961   477825417   83  Linux
/dev/sda2       956338962   967787834     5724436+   5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       956339025   967787891     5724433+  82  Linux swap / Solaris
Partition 5 does not start on physical sector boundary.
-----------------
This looks ok.  Am I wrong?

---

### Post by coldcritter64 on 2014-02-14
> **pretty_whistle said:**
> Pasting in sudo fdisk -l gave me this:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b6f69


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      688128   956338961   477825417   83  Linux
/dev/sda2       956338962   967787834     5724436+   5  Extended
**Partition 2 does not start on physical sector boundary.**
/dev/sda5       956339025   967787891     5724433+  82  Linux swap / Solaris
**Partition 5 does not start on physical sector boundary.**
-----------------
This looks ok.  Am I **wrong**?

That doesn't look too good. I'd give testdisk a thought if I had that situation, especially considering clonezilla also complained ;)

Edit: just occurred to me that the drive was restored as it is FROM a clonezilla backup originally (renoted your 1st post). What was the situation with respect to the original image being made, hardware wise specifically. That is; did you restore a clone of one drive onto a different brand with differing drive geometry etc ?

---

### Post by pretty_whistle on 2014-02-14
I bought a new laptop.  It's a 64bit and I restored a 32bit onto it.  The brand is the same though, both were HPs.

---

### Post by pretty_whistle on 2014-02-14
I see that to run testdisk I need to use the terminal.  How do I run it from there?

---

### Post by coldcritter64 on 2014-02-14
> **pretty_whistle said:**
> I bought a new laptop.  It's a 64bit and I restored a 32bit onto it.  The brand is the same though, both were HPs.

A 32 bit install to 64 bit hardware should be ok, afaik.

Assuming HP used exactly the same brand **of HDD** in both cases. Problems like this can sometimes occur when restoring to a different brand of drive (ie actual HDD brand and as such drive geometry, not HP etc. HP may be sourcing different HDDs I would normally assume).

I am not so sure my previous suggestion about testdisk is viable here as your current install comes from such an image initially.

If you do try testdisk ```
sudo testdisk
``` in terminal to run it.

---

### Post by pretty_whistle on 2014-02-14
Here's something I just found for this problem:

[http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary](http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary)

---

### Post by pretty_whistle on 2014-02-14
I've marked this thread as solved since I found that link above.

---

