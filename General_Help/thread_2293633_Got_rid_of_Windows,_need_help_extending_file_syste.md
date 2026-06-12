---
title: "Got rid of Windows, need help extending file system"
date: 2015-09-06
forum: General Help
---

### Post by Will1134 on 2015-09-06
I recently put an SSD in my old laptop (still a good machine) and I thought I wanted windows on it as it gave me what I needed to do on it. Linux turned out to have software that I needed and no longer had the problems the last time I tried to use it on this machine. So I got rid of windows. Trouble is I would like to easily extend the drive to encompass all the space (except swap and I guess the small boot partition). The "Extended" part of the filesystem seems to make expanding the space difficult. Can anyone give me a quick way of doing this?

Thanks in advance!

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1026047      512000    7  HPFS/NTFS/exFAT
/dev/sda2         1026048   145823743    72398848   83  Linux << Old OS space I want to get rid of
/dev/sda3       145825790   246161407    50167809    5  Extended
/dev/sda5       145825792   229498879    41836544   83  Linux  <<This is where the OS is and the one I want to extend.
/dev/sda6       229500928   246161407     8330240   82  Linux swap / Solari

```

---

### Post by Will1134 on 2015-09-06
Fixed it. 
The problem was that I had to resize the Extended partition first, and that couldn't be done until the swap partition was turned off. I could than resize the partition I wanted. Done all through the live CD of course.

---

