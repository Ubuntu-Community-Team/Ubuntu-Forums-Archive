---
title: "os problems"
date: 2008-03-15
forum: General Help
---

### Post by larry61 on 2008-03-15
I installed a small hard drive to load asterisk now on my main pc. it wouldn't boot the ide drive because I'm running a pair of sata's. I removed the ide drive and went to bed. When I put the pc on it still had the asterisk now in the cdrom and started loading it while I was making breakfast. to my horror it wiped out my bootloader before I could shut it off. I think the drives are okay. How can I reinstall the loader on 6.06 without messing things up further? I don't want to do a reinstall.

---

### Post by larry61 on 2008-03-15
I installed live cd an got a terminal. Typed sudo fdisk -l an got (disk /dev/sda doesn't contain a valid partition table. It is showing  start     end
                       dev/sdb1  *                 1      4314    linux
                       dev/sdb2                4315     4500   extended
                       dev/sdb5                4315     4500    swap / solaris
     Is all hope lost of recovering my info?

---

### Post by strabes on 2008-03-15
To reinstall grub see the link in my signature to the ubuntu wiki.

---

