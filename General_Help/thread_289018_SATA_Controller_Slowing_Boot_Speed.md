---
title: "SATA Controller Slowing Boot Speed"
date: 2006-10-30
forum: General Help
---

### Post by FiggyG on 2006-10-30
Hi, I have an interesting issue with my system. It appears that when booting, my SATA is being probed as a raid, even though I have the RAID option disabled in my bios. It is currently set to PATA Emulation. Do you know if there are some command I can pass to the kernel from GRUB to bypass the raid probe? The issue goes away when I disable the SATA controller completely in the bios. That is hardly a suitable solution. I am running a fresh install of Ubuntu 6.10 i386 (Same issue with 6.10 AMD64). My specs are as follows:

AMD A643000+, ASUS A8R-MVP, 200GB SATA Maxtor 7200rpm (Windows XP), 40GB PATA Maxtor 7200rpm (Ubuntu), 2x512MB Geil PC3200, ATI Radeon X1600XT, and a SB Audigy SE.

Here is part of my kernel's log file that concerns me, this is the part where it uses up more than 1 minute to probe the RAID that shouldn't be there. I have the lastest BIOS for my board.

```
[   30.455010] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 185
[   36.271026] ahci 0000:00:1f.1: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   36.271031] ahci 0000:00:1f.1: flags: ncq ilck pm led clo pmp pio slum part 
[   36.271089] ata1: SATA max UDMA/133 cmd 0xFFFFC2000003C900 ctl 0x0 bmdma 0x0 irq 193
[   36.271115] ata2: SATA max UDMA/133 cmd 0xFFFFC2000003C980 ctl 0x0 bmdma 0x0 irq 193
[   36.271139] ata3: SATA max UDMA/133 cmd 0xFFFFC2000003CA00 ctl 0x0 bmdma 0x0 irq 193
[   36.271164] ata4: SATA max UDMA/133 cmd 0xFFFFC2000003CA80 ctl 0x0 bmdma 0x0 irq 193
[   36.646637] ata1: SATA link up 1.5 Gbps (SStatus 113)
[   36.647815] ata1: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4063 85:7c69 86:3e01 87:4063 88:007f
[   36.647819] ata1: dev 0 ATA-7, max UDMA/133, 398294975 sectors: LBA48
[   36.649890] ata1: dev 0 configured for UDMA/133
[   36.649893] scsi0 : ahci
[   37.569658] ata2: SATA link down (SStatus 0)
[   67.562234] ata2: qc timeout (cmd 0xec)
[   67.562237] ata2: dev 0 failed to IDENTIFY (I/O error)
[   67.562240] scsi1 : ahci
[   68.481277] ata3: SATA link down (SStatus 0)
[   98.469854] ata3: qc timeout (cmd 0xec)
[   98.469857] ata3: dev 0 failed to IDENTIFY (I/O error)
[   98.469859] scsi2 : ahci
[   99.388897] ata4: SATA link down (SStatus 0)
[  129.381473] ata4: qc timeout (cmd 0xec)
[  129.381475] ata4: dev 0 failed to IDENTIFY (I/O error)
[  129.381478] scsi3 : ahci
[  129.381655]   Vendor: ATA       Model: Maxtor 6L200M0    Rev: BANC
[  129.381663]   Type:   Direct-Access                      ANSI SCSI revision: 05
[  129.389740] SCSI device sda: 398294975 512-byte hdwr sectors (203927 MB)
[  129.389752] sda: Write Protect is off
[  129.389754] sda: Mode Sense: 00 3a 00 00
[  129.389768] SCSI device sda: drive cache: write back
[  129.389821] SCSI device sda: 398294975 512-byte hdwr sectors (203927 MB)
[  129.389829] sda: Write Protect is off
[  129.389832] sda: Mode Sense: 00 3a 00 00
[  129.389844] SCSI device sda: drive cache: write back
[  129.389848]  sda: sda1
[  129.411911] sd 0:0:0:0: Attached scsi disk sda

```

---

### Post by pascal_belron on 2006-11-07
I got exactly the same issue, but my SATA controller is configured as AHCI. The problem is that kernel probes for every SATA channel, so as we have only one SATA drive it hangs for 1m30s (seems the timeout is 30s for one SATA channel)... 

Does anyone know if there are some kernel parameters to deactivate certain SATA channel during boot-up ?

---

### Post by DHatherley on 2006-11-22
Hi guys,

Exactly this issue on ali on-board chipset. Is this a libata issue? I'm hunting for kernel params or a way to disable selected SATA ports in the BIOS but no luck yet.

```
[17179580.800000] ata1: SATA link down (SStatus 0)
[17179610.820000] ata1: qc timeout (cmd 0xec)
[17179610.820000] ata1: dev 0 failed to IDENTIFY (I/O error)
[17179611.744000] ata2: SATA link down (SStatus 0)
[17179641.764000] ata2: qc timeout (cmd 0xec)
[17179641.764000] ata2: dev 0 failed to IDENTIFY (I/O error)
```

---

### Post by Tupoun on 2006-11-28
I have same problem with SATA. I've tried to disable non used port of SATA in BIOS but with no result.

---

### Post by ThorbjørnTux on 2006-12-02
Had this problem with my ASUS 32 MVP DELUXE with Ubuntu Edgy.

After trying a lot I finally got it working. They seems to have fixed this problem in the new kernel (which can come at any time to ubuntu)

I download kernel source 2.6.19 from 
[http://www.kernel.org/]("http://www.kernel.org/")

Then I followed the following guide to compile it:
[http://ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel]("http://ubuntuforums.org/showthread.php?t=217657&highlight=compile+kernel")

In old-config I just pressed return to everything. In x-config I marked
Device Drivers->SCSI device support->Serial ATA (prod) and PATA (experimental). The only things I changed in xconfig was:

I then added AHCI SATA support
Silicon Image SATA support
Silicon Image 3124/3132 SATA support
Uli Electronics SATA support.
And that is all (and maybe too much), but remember to have them checked (in kernel) (not doted. Kernel modules won't do - how shall the kernel read them if they can't see the hd ?)

In the bios under Main->storage configuration under 
SATA mode Selection the mode must be set to AHCI.

Now I have a lot faster boot - but my ATI 3d is gone .... 
(I have to find a way to reconfigure it with the compiled kernel).

---

### Post by 1900 on 2006-12-03
I've had the same issues with an ABit K8 system and SATA drives.

My disk drive light NEVER went out after the upgrade (and full reinstall of edgy)

I also have had an odd problem with CD & DVD burns hanging for 6 hours before starting (ide timeouts were reported every 2-5 minutes) and then writing quick and perfect (this also happened in dapper).

I went the new kernel route, except I mostly followed 

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

(after fun learning things like git(cg) well enough to 'pin' the build back to a particular 'GOOD' tag) Getting the latest and greatest always seems to get me a problematic build.)

 git clone rsync://rsync.kernel.org/pub/scm/linux/kernel/git/bcollins/ubuntu-2.6.git 

 cg-switch -r 57d8060047463ef87bc28ea3f0e5c66ec9a76538 Ubuntu-2.6.19-7.10

 AUTOBUILD=1 fakeroot debian/rules binary-debs


 
Now I'm running

2.6.19-7-ref-386 



Everything is working again, and since I used the 'Ubuntu' kernel, I 'may' have had fewer problems getting things running.

I used 'envy' to fix up my nvidia driver, and had to get a patch for vmware related to 2.6.19

I guess the good news I have is when 2.6.19 (or 2.6.20) comes out, it should fix many nasty little sata issues.

---

