---
title: "What is the right way to format a drive?"
date: 2014-12-23
forum: General Help
---

### Post by sim085 on 2014-12-23
Hello,

I have a system which previously had a Windows system. I would like to now use these drives with a Linux system. I know about "fdisk -l" and "fdisk /dev/sdX" commands and I did use them. However I had a drive with Windows installed and it seems like after restarts the OS (Ubuntu) was thinking there are still multiple partitions. I had to resort to using the dd command to wipe out everything (took ages) until this drive became "stable" and "usable".

So I was wondering if I have a pc which had Windows installed on it and I would like to now install Ubuntu (ext4) what tool / steps should I be using?

---

### Post by Bucky Ball on 2014-12-23
When you get to the partitioning section of the install choose 'Something Else'. Delete the Windows partitions, if that is what you want, and set it up the way you want it.

---

### Post by Impavidus on 2014-12-23
If you want to install Ubuntu on that drive, you could also select "use entire disk". It will wipe the disk and create new partitions. Not very sophisicated, but it will be good enough for most purposes. Or use gparted to delete Windows partitions and create Linux partitions. Most people prefer it over the command line tools, as it is very intuitive. The "something else" option of the installer also allows you to partition the disk. If the hard drive is so messed up that nothing seems to work, try zeroing out the first megabyte or so. There's usually no need to zero the entire disk.

---

