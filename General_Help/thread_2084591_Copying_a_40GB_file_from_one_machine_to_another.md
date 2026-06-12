---
title: "Copying a 40GB file from one machine to another"
date: 2012-11-15
forum: General Help
---

### Post by pwabrahams on 2012-11-15
I need to copy a 40GB file from one machine to another.  I'm using NFS and indeed it seems to do the job -- but it will probably take about 16 hours (it's still running).  I know it's not stuck because I can see the disk free space decreasing on the target machine.  

Is there a faster way to do such a copy?

---

### Post by LilLZ on 2012-11-15
Is it one file or many? Try zipping it or something. Also, using a modern usb 3.0 or thunderbolt connection would make it faster, if you have any of those things.

---

### Post by Mr_JMM on 2012-11-15
I'd be tempted to remove the HDD with the 40GB file and install it into the other machine then copy it. If you've got an eSATA port (assuming it's SATA) then job's even easier.

Other than that, next fastest I believe is USB3 drive.

---

### Post by pwabrahams on 2012-11-15
The data I want to use is just one file -- a VDI for Virtual Box.  I expect that merely compressing it will take a long time.  I don't know what the compression factor is likely to be.

---

### Post by parameter on 2012-11-15
> **pwabrahams said:**
> The data I want to use is just one file -- a VDI for Virtual Box.  I expect that merely compressing it will take a long time.  I don't know what the compression factor is likely to be.
How much free space is in the VDI? If there's quite a bit, and you zero the free space, you can use rsync with the -z option to compress the data during the transfer. Once rsync hits those zeroed blocks it will really move fast if compression is enabled.

---

### Post by coldraven on 2012-11-16
> **parameter said:**
> How much free space is in the VDI? If there's quite a bit, and you zero the free space, you can use rsync with the -z option to compress the data during the transfer. Once rsync hits those zeroed blocks it will really move fast if compression is enabled.
Well there's something that I never knew! That is why I keep coming to this forum.
Thanks

---

### Post by rnerwein on 2012-11-16
> **pwabrahams said:**
> I need to copy a 40GB file from one machine to another.  I'm using NFS and indeed it seems to do the job -- but it will probably take about 16 hours (it's still running).  I know it's not stuck because I can see the disk free space decreasing on the target machine.  

Is there a faster way to do such a copy?
hi
this is to long for 40GB. but if you are interesting to play with mount options you can 
compare the speed by using mount options. this depends on the filesystem types.
here some options which speed up the job.

noatime,nodiratime,bs=4096,barrier=0

espacally the bs size gives me much more performance.
bye
      richi

---

