---
title: "Understanding boot-repair partition advice?"
date: 2014-11-04
forum: General Help
---

### Post by debiant on 2014-11-04
Hello, 
I am running an Athlon CPU on an Asus motherboard.  I have a SATA HD (500 |Gb) with Linux Mint 17 (Mate desktop) which is still within the Ubuntu family, I think, hope you feel so too (!) and I have a 256 Gb SSD loading Windows 7 (mostly for old music stuff while I learn Ubuntu Studio on another old PC.
I'm having problems booting-I know its something to do with the new UEFI BIOS thing-or I think it is.  GRUB does not list the SSD.  In the BIOS it is there for boot override (F8 key) for the SSD and Win7 boots normally if you select it here, but it is not in the list of hard-drives in the booting order.  Also, there are multiple entries for Ubuntu as "ubuntu (UUID number)", this entry has UEFI flagged on its icon in the graphical bit of ASUS BIOS, there is also "P4 then UUID", the UEFI seems to be entered twice on the list of available drives?  The Ubuntu drive is SATA 4, the SSD is SATA 6 with a DVD in S5. I've had a good go myself including boot repair-if someone who understands this stuff better than me could have a look at this I'd be grateful!
8-[

Here is what boot-repair has done for me:

```
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.
http://paste2.org/5UMBKPK8

Boot successfully repaired.
Please write on a paper the following URL:
http://paste2.org/W9eD04Be

In case you still experience boot problem, indicate this URL to:
boot.repair@gmail.com or to your favorite support forum.
You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (500GB) disk!

The boot files of [The OS now in use - Linux Mint 17 Qiana] are far from the start of the disk. Your BIOS may not detect them.
You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk).  This can be performed via tools such as gParted. 
Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)

```

---

### Post by debiant on 2014-11-04
Going off to do a nightshift, (London, UK) if the boss isn't looking I will be on the forum later, if he is I might not see any help until tomorrow :wink:  Anyone giving me some of their precious time is always really appreciated and I do really enjoy solving problems and learning stuff here too!

---

### Post by oldfred on 2014-11-04
Best to post the link that Boot-Repair gives when you run the summary report.
Then we can see all the details.

Generally new computers are both UEFI and BIOS.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

But the two boot modes are not compatible. Or once you start booting in one mode you cannot switch to the other boot mode. And then grub menu can only boot systems installed in same boot mode.

Windows only installs and boots from gpt partitioned drives with UEFI.
Both Ubuntu & Windows only boot from MBR(msdos) partitioned drives with BIOS mode.
But Ubuntu will boot in BIOS mode from gpt but then needs a tiny 1 or 2MB unformatted partition on the drive with the bios_grub flag.

But best to always have all systems installed in same boot mode, either all UEFI or all BIOS. If not same you may have to go into UEFI and turn on/off UEFI or CSM mode to boot system installed in that mode. Some auto switch now and you can use one time boot key often f12 or f10 but depends on system.

The far from start of disk is just a standard warning. I have yet to see a newer UEFI based system have that issue. But old BIOS systems and some external USB hard drives have had issues where smaller / (root) fully within first 100GB of drive or separate /boot partition is required.

---

