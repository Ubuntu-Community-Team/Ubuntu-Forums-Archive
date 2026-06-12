---
title: "Trouble with grub"
date: 2008-06-23
forum: General Help
---

### Post by tenieldjo on 2008-06-23
I'm relatively new to the linux scene, and I wanted to learn to use it so I installed ubuntu on my laptop, and dual-booted with windows. I don't use it much on my laptop, but I decided to install it on my desktop instead and free up some extra space on the laptop. The plan was to reformat the partition and then merge it back into the ntfs part, but it wouldn't merge, and now every time I load my computer grub tries to load and gives error 21, and won't let me boot anything at all which is problematic. 

I booted the computer from the Ubuntu install disk, and tried to locate and reinstall grub, thinking it may just have been corrupted when I altered the partition, but when I ran
find /boot/grub/stage1
it was unable to find it anywhere. 

I tried to reinstall ubuntu on the blank partition, but it still loads with error 21. I'm really at a loss, this is a very new area for me and I have little experience troubleshooting anything unix-based. Any advice would be wonderful! Thank you.

---

### Post by logos34 on 2008-06-23
You need to restore the windows bootloader.  If you have a windows install cd, use that.  (>recovery console>**fixmbr**).  Or else download the Super Grub Disk.  Then use gparted from the ubuntu live cd to delete the old partition and expand windows to reincorporate the space.  (if vista, use the latter's own disk utility)

---

