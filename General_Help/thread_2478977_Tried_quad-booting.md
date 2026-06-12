---
title: "Tried quad-booting"
date: 2022-09-10
forum: General Help
---

### Post by yoitsarma on 2022-09-10
So I decided to quad-boot on my 500gb  NVME and it works. But I know there is some stuff that got messed up and i'm kindly asking if someone could look through my report and help me out? I know that I have at least 2x Kubuntu bios. Maybe if any of the file types are wrong? Let me know please!

[https://paste.ubuntu.com/p/r9ghRtvs4q/](https://paste.ubuntu.com/p/r9ghRtvs4q/)

Thanks

---

### Post by tea for one on 2022-09-10
> **yoitsarma said:**
> So I decided to quad-boot on my 500gb  NVME and it works. 

You do not have four systems on one nvme disk.
[COLOR="#0000FF"]Line 175[/COLOR] - 3 OS detected
[COLOR="#0000FF"]Line 177[/COLOR] - OS#1:   The OS now in use - Ubuntu 22.04.1 LTS CurrentSession on [COLOR="#0000FF"]nvme0n1p3[/COLOR]
[COLOR="#0000FF"]Line 178[/COLOR] - OS#2:   Pop!_OS 22.04 LTS (22.04) on [COLOR="#0000FF"]nvme0n1p5[/COLOR]
[COLOR="#0000FF"]Line 179[/COLOR] - OS#3:   Ubuntu 22.04.1 LTS on [COLOR="#0000FF"]sda6[/COLOR]

Disks sdb and sdc may contain Windows but are not detected by boot-repair.
Are they encrypted or hibernating?

---

### Post by oldfred on 2022-09-10
You show 3 ESP - efi system partitions on your NVMe drive.
Some system will not boot with that, most want one ESP per device/drive. UEFI standard does allow more than one ESP.
Vendor's UEFI is often the one that limits ESPs. Grub actually may still find and configfile boot from a FAT32 that was an ESP or directly boot kernel in other install.

Best to have all systems on a drive boot from one ESP on that drive. 
But you have to have correct ESP mounted in fstab and UEFI entry booting from that ESP.
Grub will then offer to boot every install. 
If not Ubuntu or Ubuntu based, then you may have different entries in UEFI as well which is ok.

You also have grub installed to gpt's protective MBR for BIOS boot and installed to partition's PBR(Partition Boot sector) which cannot be used to directly boot anything. UEFI systems should not have grub in MBR, but erasing it may be dangerous unless knowledgeable on safe use of dd. And grub should never be installed to a partition. Grub2 does not fit on a partition correctly, needs blocklists,  and can only be used from another grub.

---

### Post by HermanAB on 2022-09-11
Why? I would suggest using a virtualizer instead, ie with Gnome Boxes.

---

