---
title: "Copying and zeroing a drive"
date: 2007-04-24
forum: General Help
---

### Post by SishGupta on 2007-04-24
I recently purchased a 320gb drive which is defective. It reads and writes fine but it makes a funny noise and it was recommended by the online store that I bought it from that I return it. They are shipping me a replacement and then I ship this one back.

1. I want to make a 1:1 copy of this drive. What is the best/fastest way? I want everything, all partitions and the mbr if possible.

2. How do I completely erase all data on this drive? At best I'd like to write 0's to the drive but if this takes too long I'd be willing to settle for a trade off solution. I would like my data to be unrecoverable.

Thanks

---

### Post by kh4nh on 2007-04-24
Hi there,

> **SishGupta said:**
> 
1. I want to make a 1:1 copy of this drive. What is the best/fastest way? I want everything, all partitions and the mbr if possible.


This not the fastest way. IMO, it's the best way. Warning: this may take a long time.

dd if=/dev/"name of the source drive" of=/dev/"name of the destination drive" bs=10K

# source drive: the defective drive that you are returning 
# destination drive: the new drive that they are sending


> **SishGupta said:**
> 
2. How do I completely erase all data on this drive? At best I'd like to write 0's to the drive but if this takes too long I'd be willing to settle for a trade off solution. I would like my data to be unrecoverable.


you can ovewrite you files with shred
sudo shred -vfz -n 3 /dev/"name of the drive"

# -n 3: tell shred to overwrites the contents of the disk 3 times, you can specify any time you like


Hope that will help you,

---

### Post by SishGupta on 2007-04-25
thanks!

---

### Post by kh4nh on 2007-04-25
No problem. I almost forgot. If you throw in "-u" option, shred will truncate and remove all the files.

shred -vfzu -n 3 /dev/"hard drive"

#v: verbose
#f: force to overwrite
#z: write zero at last

---

