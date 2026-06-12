---
title: "Missing partition"
date: 2007-10-19
forum: General Help
---

### Post by Nevon on 2007-10-19
I'm dual booting Windows XP and Ubuntu 7.10. I have two partitions with the different OSs on, and the swap. Then I had 200gb of unallocated space, which I wanted to use for storage. So I downloaded some ntfsprogs, which extended gparted, then I used gparted to make an ntfs partition. 
Windows can find it, but Ubuntu doesn't. 
Help, please?

---

### Post by Light- on 2007-10-19
does it show up in /dev as a separate hard drive?

if so, you can mount it by using mount -t ntfs /dev/<drive>

---

### Post by Nevon on 2007-10-19
No, it shows up as a separate partition, called sda4. 
I just can't find it in "my computer", on the desktop or in /media.

EDIT: Lol! I found it in the list of available disks in Deluge, and all of a sudden it pops up everywhere as "disk".

---

