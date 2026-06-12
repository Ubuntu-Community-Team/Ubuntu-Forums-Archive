---
title: "Can't mount after Grub starts..."
date: 2006-12-10
forum: General Help
---

### Post by Andreu22 on 2006-12-10
Hi 

I have a recent grave problem :( , I had a stable Ubuntu configuration that worked very well, but since I re-installed Win2, I had removed grub, which I repared quickly thants to The Super Grub Disk software, but, it appears that after starting normaly, it can't go on because it can't mount / , :confused: I guess it refers to the partition where linux is, but I am just a new user, a beginer in linux, and so I do not know how to solve this problem without re-installing Ubuntu, and this is not an option, because I have a lot of information inside...

Please, help me, if you all are so kind, :p 

Regards from Barcelona,

Andreu

---

### Post by bulldog on 2006-12-10
Boot from the live cd and mount your ubuntu install.
To find your ubuntu partition```
sudo fdisk -l (l as in like)
```and copy the outcome to the forum.
Than we will mount your ubuntu to have a look at your problem.

---

### Post by Andreu22 on 2006-12-10
Thanks, :-D 

Here it is:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13262   106526983+   7  HPFS/NTFS
/dev/sda2           13263       17334    32708340   83  Linux
/dev/sda3           17335       17511     1421752+   5  Extended
/dev/sda4           17512       19457    15631245    b  W95 FAT32
/dev/sda5           17335       17511     1421721   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by Andreu22 on 2006-12-10
Any guess about what I can do...?

---

