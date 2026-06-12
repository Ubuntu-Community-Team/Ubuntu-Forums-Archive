---
title: "Lubuntu as guest on Virtualbox USB drive not recognised"
date: 2016-03-28
forum: General Help
---

### Post by rdh61 on 2016-03-28
Hi,

I am have installed Lubuntu 15.10 as a guest OS on Virtualbox on a machine running Windows 10 as the host OS.

I have enabled my guest system to recognise two USB pen drives, but only one of them is ever recognised. The other one never is. I only plug in one of them at any one time.

Any ideas?

Thanks.

---

### Post by rdh61 on 2016-03-28
I must add that I have installed VirtualBox Extension Pack and Guest Additions.

---

### Post by ajgreeny on 2016-03-28
Are both pen-drives formatted as fat32 or something different?
If one is NTFS, was it removed properly from the last Windows OS in which it was used?  If not the NTFS partition will still be flagged as "In use" and therefore not mountable in Linux.

---

### Post by rdh61 on 2016-03-29
Thanks for you reply. Both pen drives are FAT32.

---

