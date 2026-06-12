---
title: "Error 28 : selected item cannot fit into memory"
date: 2008-02-24
forum: General Help
---

### Post by Najmudin on 2008-02-24
I purchased a new desktop recently equiped with 3 hard drives 500 GB ,160 and 160 GB,with Intel Core 2 Duo 2.20 Ghz and 2 GB Memory,Windows XP is installed in a partition of the 500 GB drive ,I installed ubuntu 7.10 on one of the 160 drives.
But after finishing the installation i get into memory problems like when i minimize , maximize a window while playing a sound or music it was hanging the playing for a while then continue , the system was slow also , so i reinstall it but i get the same problem , later i installed ubuntu studio which has a different kernel  ( 2.6.22-14-rt) the problem was reduced and I'm still using it but I'm not comfortable with ubuntu studio and want to return back to the original gutsy.
I noticed that when i try to do a memtest in grub screen i get this error:
> Error 28 : selected item cannot fit into memory
So think my problem is with the memory or kernels (not sure), but just don't know what to do to solve the problem.:(
Today I tried to install Linux Mint based on gutsy on the other 160 drive which is free , and i get the same problems :mad: so i delete it again and decided to write this post hoping that some one can help me with it.
Notice : 
- my old desktop was working great with gutsy and feisty without these troubles.
- XP is working fine on the new one also.
- if i use a live cd i can do a memtest but after installing it i cant.
Sorry for the long post .

---

### Post by Najmudin on 2008-02-25
Any Idea :neutral:

---

### Post by kubug on 2008-05-16
I have the same problem. Can't use memtest. I don't have the other issues you mentioned, though. 

One thing I do want to mention is that I have 2 harddrives in RAID, and I dual-boot into WinXP as well. So I use dmraid to do that. Does it have anything to do with that?

Oh... and my kernels don't update either. They download and install, but GRUB doesn't change it. I always boot with the old kernel.

---

### Post by zdea on 2008-06-21
It must be somethign with the dual-boot dmraid thing because I have that setup as well and All new kernels since .16 in hardy will not boot, they crash along the way, however .16 works fine. Memtest also yields this error 23 thing. I'm looking for a solution but can't seem to find one yet.

---

### Post by atarianer on 2008-06-25
Have the same error Message on my Notebook, but the cause is obviously the installation of Safeguard Easy on the WindowsXP partition.
So looks like the bootimage or something else is now encryptet and thus looks "corrupted" to grub :/

---

