---
title: "end_request I/O error, dev sda, sector 442933180 - best strategy to repair?"
date: 2016-10-22
forum: General Help
---

### Post by HilliBilly on 2016-10-22
Experienced an electricity shortcut during booting ... which seems to have damaged my hard disk?

Now, system does not boot any more (Actually, it's a dual boot system: Windows XP does boot without problem, Ubuntu 11.04 does not). I made two pictures from the error messages shown on the screen. 

> 
[FONT=Courier New]ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata3.00: BMDMA stat 0x24
ata3.00: failed command: READ DMA EXT
ata3.00: cmd 25/00:00:bb:9f:66/00:001a:00:00/e0 tag 0 dma 4096 in
         res 51/40:00:bc:9f:66/40:00:1a:00:00/e0 Emask 0x9 (media rror)
ata3.00: status { DRDY ERR }
ata3.00: error: { UNC }
end_request: I/O error, dev sda, sector 442933180
[/FONT]



I tried to boot from the LiveCD and manually run fsck but this did not solve the problem:

> [FONT=Courier New]root@ubuntu:/# fdisk -l

Disk /dev/sda: 298.1 GiB, 320071851520 bytes, 625140335 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xaa26aa26

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *           63 316464434 316464372 150.9G  7 HPFS/NTFS/exFAT
/dev/sda2       316464435 613056464 296592030 141.4G 83 Linux
/dev/sda3       613056465 625137344  12080880   5.8G  5 Extended
/dev/sda5       613056528 625137344  12080817   5.8G 82 Linux swap / Solaris



root@ubuntu:/# fsck /dev/sda2
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sda2: clean, 396175/18546688 files, 33752637/37074003 blocks
root@ubuntu:/# [/FONT]

[edited: just spelling mistakes)

---

### Post by Bashing-om on 2016-10-22
HilliBilly; Ouch;

Bad things do happen. a fact of life as we know it.

Look, release 11.04 is long past End_Of_Life and there is no ready access to any files that might be required to fix this install.

What I do recommend is to run a smart test on the drive from a liveDVD, and if the drive reports as healthy - save your personal data and install a current release .
```

sudo apt-get install smartmontools
sudo smartctl --all /dev/sda

```
tutorials on understanding the outputs :
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335)

[INDENT][INDENT]all good things can come to an end
[/INDENT][/INDENT]

---

