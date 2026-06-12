---
title: "Copying image went wrong - all data lost"
date: 2007-07-01
forum: General Help
---

### Post by larsa on 2007-07-01
Hi.

I  tried to install 'USB Pendrivelinux' to my pen drive some minutes ago. Following [this]("http://www.pendrivelinux.com/2007/05/16/usb-pendrivelinux-install-tutorial/#more-219") guide, something wrong happened. After a restart of Ubuntu, I were ready to try again. Sure that the mountpoints hadn't changed, I started with point 7 of the guide. Before had the pen drive 'sde', but now the portable hard drive at 500GB.
```
7. Type dd if=pendrivelinux.img of=/dev/sdX
```
The copying went slower now than last time. I saw the portable hard drive was blinking,  and afterwards checked the disk. As i thought, the disk was formatted, and in the partition manager (Gparted) there was a new partition at ~400MiB. The rest was deleted, and put as unallocated (464.3GiB). The device was a NTFS-formatted disk before this happend.

I really want my data back; So a big thanks to everyone which could help me.

---

### Post by tillo on 2007-07-01
I can not help you, but I work in IT security, and I can tell you that what you want to do is really, really difficult. If you don't know someone who has experience in computer forensics or knows some excellent recovery software, your data is gone.
Oh, and until you find that guy, just don't touch anything on that disk: any consequent modification can screw up the recovery.

---

### Post by larsa on 2007-07-01
Oh, but thanks for the answer. I think I'll go for one of the recovery-programs which are easily found at Google, and try to get back something, even it most likely would be damaged.. 

Any tips for a good and easy-used application for recovery?

---

### Post by tillo on 2007-07-01
I don't have names in mind, but I know that there are free and easy to use programs to retrieve data on disks which have lost *part or complete meta-data information* -- that is, the file system structure and index or the partition table data.
But what you want to do is completely different: you want to retreive the last value which has been set on 500GB's worth of sectors of your disk. I don't think there are free choices... but good luck anyway :D

---

