---
title: "After install, Windows doesn't appear as a boot option"
date: 2013-07-03
forum: General Help
---

### Post by Duncanpainter on 2013-07-03
Hi everyone! I've just installed ubuntu on my desktop and love it but I've hit a bit of a problem. On my computer I have one SSD that I installed Windows 8 on and a HDD that is used to store all my files(I have some very large photoshop/image files). When installing ubuntu I chose to partition the SSD and install it on there and all has gone well. I partitioned the SSD while loading on ubuntu and gave it 30GB space which is more than I need for it but my issue is when I turn on my computer it loads ubuntu by default and I now cant find my bootable Windows 8 partition. I can only see my SSD and HDD in the BIOS and not the individual partitions. Any ideas? It's not a big deal for now but I will need Windows back at some point in the near future!

Thanks in advance for your help!

---

### Post by oldos2er on 2013-07-03
Can you open a terminal (Ctrl-Alt-t) and enter ```
sudo fdisk -l
``` and copy and paste the output here? This commands lists all your hard disks and their partitions.

---

### Post by fantab on 2013-07-04
Is it a Laptop or Desktop? what brand and model? Was Windows8 pre-installed? If it came pre-installed then the chances are its booting from EFI partition. Is it?

Post the output of **[BootInfo Script]("http://bootinfoscript.sourceforge.net/")**.

---

### Post by Duncanpainter on 2013-07-07
Hi, here is the results of sudo fdisk -l


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbc0abc0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    60200478    30100208   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c683c67

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321    7  HPFS/NTFS/exFAT


I  guess by looking at that it hasn't partitioned properly but if I look  at Propoties of the Home folder it only shows 25GB left which makes  sense considering I only gave 30GB to Linux.

> **fantab said:**
> Is it a Laptop or Desktop? what brand and model? Was Windows8 pre-installed? If it came pre-installed then the chances are its booting from EFI partition. Is it?

Post the output of **[BootInfo Script]("http://bootinfoscript.sourceforge.net/")**.
Hi, it's a desktop that I've built my self and I installed Windows 8 on it.

---

### Post by fantab on 2013-07-07
> **Duncanpainter said:**
> Hi everyone! I've just installed ubuntu on my desktop and love it but I've hit a bit of a problem. On my computer I have one SSD that I installed Windows 8 on and a HDD that is used to store all my files(I have some very large photoshop/image files). When installing ubuntu I chose to partition the SSD and install it on there and all has gone well. I partitioned the SSD while loading on ubuntu and gave it 30GB space which is more than I need for it but my issue is when I turn on my computer it loads ubuntu by default and I now cant find my bootable Windows 8 partition. I can only see my SSD and HDD in the BIOS and not the individual partitions. Any ideas? It's not a big deal for now but I will need Windows back at some point in the near future!


Since you didn't post the output of 'BootInfo script' it will be hard to tell what is going on with Grub.

**[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")** tool is quite adept at fix the kind of issue you are having. Its a known bug where Grub uses a wrong entry for Windows, (but this was with UEFI).
Try Boot-Repair and run the 'Recommended Repair' and see if it helps. If it does not then post the link which 'BootInfo Summary' generates, this should give us pretty good idea of your Boot process.

---

### Post by Penguenci on 2013-07-07
Have you installed GRUB on the very partition you installed Ubuntu, or on the MBR? The former can cause problems at times.

First try this on the terminal:

```
sudo update-grub
```

It's the simplest solution, and will typically work if the problem is simple.

There is a cute little application called GRUB Customizer, which will let you customize your GRUB configuration in detail, and will typically show you the missing OS entries and add them to your GRUB menu for you. You could try that one as well.

If none of those work, your problem is on the complicated side, and you'd need Boot-Repair. Going for the recommended repair usually fixes the problem with the mere exception of mapping issues afaik.

Note that all those solutions assume you didn't destroy the Windows partition and/or boot sector somehow. The Windows 8 Loader has to be present and the partition must be healthy, otherwise your solution lies within Windows itself, not Linux.

To make sure it's still there, you could try installing a third party bootloader such as Paragon, and see if it detects your Win8 installation. If you're running multiple HDD's, I recommend installing the GRUB loader on the SSD MBR, and Windows loader on the HDD MBR, just to be on the safe side should something fail unexpectedly.

---

### Post by gordintoronto on 2013-07-07
One small suggestion for future reference: you get better help if the subject of your thread describes the problem, such as "After install, Windows doesn't appear as a boot option.

---

