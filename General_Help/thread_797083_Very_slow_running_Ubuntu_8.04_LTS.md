---
title: "Very slow running Ubuntu 8.04 LTS"
date: 2008-05-16
forum: General Help
---

### Post by martyh99 on 2008-05-16
I was running RedHat 9 but decided to get modern and installed Xubuntu 8.04 LTS on the same hardware pc. But it is much slower than when I was running RedHat.
Also when Ubuntu 8.04 LTS was installing it changed my IDE 20 Gb drive disk name from hda to sda!!??

1) How come it did that?

2) How come my pc is running very slow under Ubuntu 8.04 LTS?

Some googling seem to indicate that it might have something to do with that way 8.04 changed the drive types from IDE to some sort of scsi type emulation - why it did that is a big mystery to me!! and the Ubuntu community seemd to be very silent about as well!!

The command currently show this,
# sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:    42 MB in  2.02 seconds =  20.81 MB/sec
 Timing buffered disk reads:   14 MB in  3.37 seconds =   4.16 MB/sec

The command uname shows,
# uname -a
Linux xubuntu-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

I really need some direction on this!

Thanks in advanced.

---

### Post by mikewhatever on 2008-05-17
> 1) How come it did that?

The convention of naming hdds was changed starting from Edgy Eft, so that both sata and ide are sd and not hd.

> 2) How come my pc is running very slow under Ubuntu 8.04 LTS?

Don't know. What are the specs of your PC?

---

### Post by martyh99 on 2008-05-17
CPU:  CPU0: Intel Pentium III (Coppermine) stepping 0a
Intel Celeron 851.923 MHz processor

Memory: 361508k

Hard Drives (listing from /var/log/message):
ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
ata1.00: ATA-5: MAXTOR 4K020H1, A08.1500, max UDMA/100
ata1.00: 39876480 sectors, multi 16: LBA
ata1.01: ATA-4: WDC AC14300R, 17.01J17, max UDMA/66
ata1.01: 8421840 sectors, multi 16: LBA
ata1.01: limited to UDMA/33 due to 40-wire cable
ata1.00: configured for UDMA/66
<< snippet >>
ata2.00: ATAPI: LG CD-ROM CRD-8522B, 2.01, max MWDMA2
ata2.00: configured for PIO4
scsi 0:0:0:0: Direct-Access     ATA      MAXTOR 4K020H1   A08. PQ: 0 ANSI: 5
scsi 0:0:1:0: Direct-Access     ATA      WDC AC14300R     17.0 PQ: 0 ANSI: 5
scsi 1:0:0:0: CD-ROM            LG       CD-ROM CRD-8522B 2.01 PQ: 0 ANSI: 5
Driver 'sd' needs updating - please use bus_type methods
sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 0:0:0:0: [sda] 39876480 512-byte hardware sectors (20417 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sda: sda1
sd 0:0:0:0: [sda] Attached SCSI disk
sd 0:0:1:0: [sdb] 8421840 512-byte hardware sectors (4312 MB)
sd 0:0:1:0: [sdb] Write Protect is off
sd 0:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
sd 0:0:1:0: [sdb] 8421840 512-byte hardware sectors (4312 MB)
sd 0:0:1:0: [sdb] Write Protect is off
sd 0:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA


# sudo lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 21)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 83)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:0b.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 25)
00:0f.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0f.1 Communication controller: C-Media Electronics Inc CM8738 (rev 20)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 21)

---

### Post by lvella on 2008-05-28
I just installed Ubuntu 8.04 and noticed the same problem.

I was using an unstable version of Debian and noticed the change from hda to sda on some kernel update. Despite the trouble it caused with the computer configuration, there was no noticeable performance change.

Now I installed Ubuntu 8.04 and hard disk seems to be considerably slower.

---

### Post by ori2on on 2008-07-23
> **lvella said:**
> I just installed Ubuntu 8.04 and noticed the same problem.

I was using an unstable version of Debian and noticed the change from hda to sda on some kernel update. Despite the trouble it caused with the computer configuration, there was no noticeable performance change.

Now I installed Ubuntu 8.04 and hard disk seems to be considerably slower.
I have the same problem
Running xubuntu 8.06
1 GiB
2 Ghz

When browsing, everything goes fine, until maybe 10 minutes, the CPU goes from 20 to almost 100%, an everything goes extremely slowly. 

When restarting the computer, or the browser (firefox), especially letting the computer rest (20.30 min) the problem dissappear, for then to come back after approx. 10-15 min

---

### Post by salemboot on 2008-07-27
Can one of the Ubuntu kernel developers rethink this policy change?

hdparm -c1 -u1 /dev/sda  <-- Not going to work anymore.


What this entails is that we are going to get reduced performance with IDE hard drives.  If this is across the board meaning all **buntu** products as well **debian** unstable then you can expect angry people.

So that I can repair the damage here was this a scsi-emulation hack?

A link to a post would help as well.

It seems given hdparm won't operate on the device that they hacked the sata drivers and made them operate on IDE.


Thanks,

**update**
I found the following thread.  [http://ubuntuforums.org/showthread.php?t=415057](http://ubuntuforums.org/showthread.php?t=415057)

You have to set "hwprobe=-modules.pata" 

-=-=-=-= THE ARTICLE CARE OF SUSE =-=-=-=-=-=-==
[http://www.softwareinreview.com/linux_optimizations/hacking_opensuse_10.3.html](http://www.softwareinreview.com/linux_optimizations/hacking_opensuse_10.3.html)

[I]DVD mounting and playback problems, IDE hard drive performance issues

A problem with openSUSE's ATA driver may cause some people with parallel ATA (IDE) hard drives to experience performance problems, and CD/DVD drive issues. There's a quick fix for this that is easy to test. Restart your computer, and when you get to the green openSUSE boot screen, type this in:

hwprobe=-modules.pata

The letters you type should show up in a field near the bottom of the screen. Press Enter to boot your system with the new option. If the problem goes away, you will need to add this option to your GRUB configuration permanently. To do so, start YaST (for instructions on how to do this, see other parts of this guide) and click on the System tab, then Boot Loader Configuration. Click Edit to modify the default configuration, then type in the same line shown above in the Optional Kernel Command Line Parameter field. There will be other settings in this field as well. Just add a single space after the last setting, then type the same line you typed in at the boot splash screen.[/I]
-=-=-=--=-=


Rage Level [****--]

---

### Post by salemboot on 2008-07-29
I think this solves the issue.

[http://www.linuxquestions.org/questions/linux-general-1/which-kernel-config-option-shows-hda-as-sda-594516/](http://www.linuxquestions.org/questions/linux-general-1/which-kernel-config-option-shows-hda-as-sda-594516/)

---

### Post by PCFascist on 2008-08-21
I agree... 8.04 is running dog slow for me as well. I'm unsure why but I have see my memory usage max out? 
This doesn't seem to be the issue as my other box has only 15mb free of 2gb...

I happened to upgrade... I guess this has something to do with it.

---

### Post by Hal58 on 2008-09-03
8.04 is slow due to not setting the UDMA mode correctly.  I posted log extracts from several of my systems which all say UDMA/33, many due to 40-wire cable, even where the cable is in fact 80-wire, or N/A such as an EeePC with the onboard Solid-State Disk with NO cable, or a Transcend 300x Compact Flash which should be in the 45-50 MB/s range, and a 266x CF on a SATA adapter.  Several of these systems performed much faster with the earlier 7.04 Feisty Fawn release, but now are dogging down.

--
Don't anthropomorphize your computer, it doesn't like it.

---

