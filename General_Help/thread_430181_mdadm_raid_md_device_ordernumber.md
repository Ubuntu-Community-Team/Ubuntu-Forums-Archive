---
title: "mdadm raid md device order/number"
date: 2007-05-01
forum: General Help
---

### Post by icpeanuts on 2007-05-01
I am new to linux and ubuntu. I am trying to setup 4 raid1 sets. md0, md1, md2, md3

md0 is the "/" partition
md1 is the swap partition
md2 is the /home partition
md3 is a large raid 1 I am using as a file server drive.

md0 to md2 are partitions of ide drive.
md3 is a sata drives

When I create the raid1 sets, it works fine. Everything works until I reboot the system. For some reason, the sata raid 1 (md3) becomes md0. Grub can not boot, I have to edit the boot file and change the boot partition to md1 instead of md0.

For some reason, ubuntu changes the md devices md0 becomes md1, md1 becomes md2, md2 becomes md3 and md3 becomes md0.

I looked and can not find a solution to fix this problem. I want to keep the original md devices order/numbering. I tried using UUID in the fstab, but it does not work. On boot, md devices are out of order. 

I want to know if there is a way I can fix this so that the system keep the orginal md devices I configured. 

Thanks

---

### Post by jwbaker on 2007-05-02
How is the root device specified on the kernel command line?  You can use UUID there, too.  For example: root=UUID=4a6aed11-42dd-4c82-81ce-8f469e93f210

Aside from that, you might do a dpkg-reconfigure mdadm, and tell it that you want ALL raids started from within the initrd.

In general you can't rely on the naming of those devices.

---

### Post by icpeanuts on 2007-05-02
Thanks, I tried that, it did not work.
When I did the boot using the UUID, it just hang
I did the dpkg-reconfigure, nothing change.
The naming of the md0, md1,md2, md3 are still out of order. I just want to make it so md0 is md3, md1 is md0, md2 is md1, md3 is md2 - the way I originally set it up.

---

