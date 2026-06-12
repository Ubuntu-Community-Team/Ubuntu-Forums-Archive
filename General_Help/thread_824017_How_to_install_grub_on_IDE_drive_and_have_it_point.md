---
title: "How to install grub on IDE drive and have it point to Ubuntu on SATA due to BIOS"
date: 2008-06-09
forum: General Help
---

### Post by garethsimpsonuk on 2008-06-09
I've been trying to install ubuntu on a SATA drive on an IDE based mobo using a pci SATA controller. I thought my bios would suppport it as I have an entry in boot priority to boot from 'add in card'.

Turns out I it wont. The installer recognises it fine and I can install to it but the bios wont pick it up at boot. 
I think the solution is to install grub on the IDE drive and have it point to the kernel on the SATA. I don't know how to do this and hope someone can help me.

How big do I make the partition? 
Some have said that installing /boot to a drive automatically installs it in the MBR but if you can choose the partition size how is that possible when the MBR is a set size.
Do I just go into the grub menu and make an entry to point to the kernel? What entry? 
Do I have to set the /boot partition to an exact size? 
Do I have to install it first at the beginning of the drive?

Any help would be much appreciated as I really wanna have my root on the SATA for better performance!

Cheers

---

### Post by garethsimpsonuk on 2008-06-09
bump

---

### Post by cdtech on 2008-06-09
The dev has to be bootable (flaged). You can sudo grub-install /dev/hda (whatever your device is). This will install grub on that device, then you'll need to edit the menu.lst accordingly. I haven't tried it myself but it should work, right?

---

### Post by garethsimpsonuk on 2008-06-10
ok excellent then i just go into the grub menu at boot, and use the correct syntax to point to the kernel?

---

### Post by garethsimpsonuk on 2008-06-10
bump

---

### Post by garethsimpsonuk on 2008-06-10
can someone please tell me what I put in grub? Here is my partition info:

PATA
SDA1 /boot 9MB
SDA2 /media/storage 80GB

SATA
SDB1 /root 8GB
SDB2 /swap 2GB
SDB3 /home 193GB

I need to have grub on the IDE's MBR so the bios detects it. Then grub will boot to the SATA.

Any help would be much appreciated. Cheers guys

edit: would making a bootloader floppy help my situation? ( something to do with the cylinders not being 1024 on the hd )

---

### Post by garethsimpsonuk on 2008-06-10
wow I was installing the setup as above and I get an error:

> An error was returned while trying to install the kernel into the target system.

Kernel Package: 'linux server'.

Check /var/log/syslog or see virtual console 4 for details.

When I check terminal 4 there's a page of errors about dependencies

---

### Post by garethsimpsonuk on 2008-06-10
bump

---

### Post by garethsimpsonuk on 2008-06-10
I've been trying to install ubuntu on a SATA drive on an IDE based mobo using a pci SATA controller. I thought my bios would suppport it as I have an entry in boot priority to boot from 'add in card'.

Turns out I it wont. The installer recognises it fine and I can install to it but the bios wont pick it up at boot.
I think the solution is to install grub on the IDE drive and have it point to the kernel on the SATA. I don't know how to do this and hope someone can help me.

How big do I make the partition?
Some have said that installing /boot to a drive automatically installs it in the MBR but if you can choose the partition size how is that possible when the MBR is a set size.
Do I just go into the grub menu and make an entry to point to the kernel? What entry?
Do I have to set the /boot partition to an exact size?
Do I have to install it first at the beginning of the drive?

Any help would be much appreciated as I really wanna have my root on the SATA for better performance!

Cheers

---

### Post by Titan8990 on 2008-06-10
You can just make a say 500MB partition on the IDE drive. During installation set it's mount point to /boot like you mentioned and that where grub will be installed and the system will boot from.

Set the SATA drive's partition to mount at /. That should be all there is to it.

---

### Post by unutbu on 2008-06-10
You don't need to make a /boot partition.

You can install GRUB on the primary IDE drive's MBR and simply have it point to the partition on the SATA drive which contains your /boot/grub/menu.lst. You can edit menu.lst to give you options to boot multiple OS's.

I would try this before making a /boot partition because it is simpler. If it doesn't work, then you could try the /boot solution.

Here are instructions on how to setup GRUB:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The important thing to understand is that the GRUB command

```
root (hd?,?) 
```

should refer to the partition which contains your Ubuntu root partition (with the /boot directory), but the

```
setup (hd0)
```

command should point to the primary hard drive that the BIOS is handing off to during the boot process.

---

### Post by issih on 2008-06-10
Ok, I at least am confused as to what you are doing.

I thought you had windows on the ide drive directly connected to the motherboard, and then had ubuntu on the sata disk connected via a sata pci card. 

If that is the aim then what you need to do depends on whether grub installed into the master boot record (mbr) on the ide drive can see the sata drive at all.

Grub consists of various stages, the first of which is installed directly into the mbr of a drive, it then offloads onto the next stage, which can be just about anywhere provided the bios lets grub see the drive containing the files.

in theory grub can be installed on one drive and boot ubuntu from another (in fact one of my boxes does just this) but I don't know if grub will be able to direct to your sata drive until a kernel is loaded.

If grub can't access the sata drive (your best bet to find out is probably to try playing with a supergrub disk.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and see if it can boot the ubuntu partition.

If the bios simply isn't making the sata drive available at all, then your only option is to create a boot partition on the ide drive, this will contain the files necessary to boot the linux kernel, which will then provide access to the sata disk. The rest of the boot procedure is then carried out by redirecting to the sata drive.

Basically I'd get a copy of supergrub disk, see if that can boot ubuntu for you, if it can then I think you ought to be able to make it work simply by installing grub onto the mbr of the the ide drive.

---

### Post by garethsimpsonuk on 2008-06-10
no this box is pure ubuntu, it just wont boot the SATA.

Yea I want to install grub on the IDE MBR to point to the kernel on the SATA. What size do I set the grub partition and don't I have to change the cylinder size?

---

### Post by garethsimpsonuk on 2008-06-11
bump...still stuck if anyone can help

---

### Post by meierfra. on 2008-06-11
Are you able to boot Ubuntu with SuperGrub? Does SuperGrub detect your Sata drive? If not, you will have to create a  boot partition on your IDE drive (that is, the kernel needs to be stored on the IDE drive)

[URL="http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"]
How to make a dedicated grub partition[/URL]
[URL="http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition"]
How to make a separted boot  partition[/URL]

---

