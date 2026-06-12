---
title: "faulty external HD"
date: 2018-05-02
forum: General Help
---

### Post by Robbyx on 2018-05-02
My friend's external HD is formatted to NTFS. It has just one partition.  It has some errors on it. Before I try to repair them using Window's chkdsk, she has been told that the damaged drive should be cloned to a new drive copying via bit to bit. She bought a new External HD of the same size as the corrupted one. The os is Ubuntu 14.04. 

What is the easiest  way to clone the old corrupted drive  to the new drive?

---

### Post by yancek on 2018-05-02
Use the dd command for bit for bit copying.  The link below gives a basic explanation with some examples of the commands to use.

[https://linoxide.com/linux-command/linux-dd-command-create-1gb-file](https://linoxide.com/linux-command/linux-dd-command-create-1gb-file)

---

### Post by Robbyx on 2018-05-02
Thank you for the referral. 

The first example looks most appropriate as it allows copying of a drive to another drive bit to bit:

# dd if=/dev/sda of=/dev/sdb bs=4096 conv=noerror,sync
97281+0 records in
97280+0 records out
99614720 bytes (100 MB) copied, 2.75838 s, 36.1 MB/s

Where do I get the value for bs?

---

### Post by Robbyx on 2018-05-02
**Where do I get the value for bs?**

Whilst waiting for a reply I have done some searching on BS for dd and coming to the optimum size seems quite difficult. Following the advice at 

[https://superuser.com/questions/234199/good-block-size-for-disk-cloning-with-diskdump-dd#234204](https://superuser.com/questions/234199/good-block-size-for-disk-cloning-with-diskdump-dd#234204)

According to a commentt in that answer the bs is the size of the memory used for  storing each  disk area copied before writing to the new location.it doesn't seem to be the actual size of the block on the destination disk.

I propose to use bs = 64. Any strong objections?

---

### Post by QIII on 2018-05-02
That will take a good deal more time because you increase the number of operations, but there is certainly no harm in it if you pour a larger cup of coffee.

:)

---

