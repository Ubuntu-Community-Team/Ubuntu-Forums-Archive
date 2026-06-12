---
title: "How to run a different partition on startup?"
date: 2008-06-09
forum: General Help
---

### Post by daltonlaffs on 2008-06-09
Hello everyone,

I've been using Ubuntu on an external HD for quite a while now, and I've decided that I want it and Windows Vista to cleanly dual-boot on a system. I'll install Vista first, then Ubuntu on a separate partition. Here's the partition table of my primary drive:

- /dev/sda1: "PQSERVICE" (ntfs) 9.76GB
- /dev/sda2: "ACER" (ntfs) (active drive) 69.78GB
- /dev/sda3: Unnamed (ext3) 19.53GB (WILL BE USED FOR UBUNTU INSTALL)
- /dev/sda4: "PQS2" (fat32) 10.74GB

I NEED to autoboot from the /dev/sda4 partition when my computer starts, because it contains my Windows Vista restore software. How can I do this?

Thanks in advance!

---

### Post by Vivaldi Gloria on 2008-06-09
If you are using Ubuntu's boot loader GRUB then in general you edit 

```
 /boot/grub/menu.lst 
```

to change the boot options. So read around about menu.lst. 

If it was a Windows partition rather than a Windows Restore partition then it could be easily done by chainging menu.lst. But I don't know anything about Windows restore so I don't know if it can be used by chainging menu.lst.

Search for windows restore and menu.lst in the forums.

---

