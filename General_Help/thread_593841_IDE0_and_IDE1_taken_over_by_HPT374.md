---
title: "IDE0 and IDE1 taken over by HPT374"
date: 2007-10-27
forum: General Help
---

### Post by Etlaesium on 2007-10-27
Hi all...

I am having a serious problem relating to my on-board IDE controller vs. my HighPoint RocketRAID controller.  These symptoms happened when upgrading to Gutsy.  Same happens when using the Gutsy LiveCD (I get BusyBox after seeing the install screen no matter which CD/DVD-rom I use).  With Fiesty, I get hda, hdb, hdc, hdd, hde, hdg, hdi, and hdk.

My physical setup is:

IDE0 Master -: Fujitsu IDE Harddrive
IDE0 Slave   -: Generic ATAPI CD-ROM
IDE1 Master -: HP CDWriter
IDE1 Slave   -: MSI DVD-ROM

On my HighPoint card:
SATA1 -: Seagate 160GB SATA
SATA2 -: Seagate 250GB SATA RAID5 Member
SATA3 -: Seagate 250GB SATA RAID5 Member
SATA4 -: Seagate 250GB SATA RAID5 Member

When I start Ubuntu, the following assignments take place:
SATA1 = IDE2 (hde)
SATA2 = IDE3 (hdg)
SATA3 = IDE0 (hda)
SATA4 = IDE1 (hdc)

Then...
"VP_IDE: too many IDE interfaces, no room in table"
"VP_IDE: too many IDE interfaces, no room in table"
"VP_IDE: neither IDE port enabled (BIOS)"

*** IDE0 and IDE1 are enabled in BIOS ***
Also, the jumpers are set properly on the IDE drives.
...The drives show up in BIOS.
...The lights activate properly on all removable media drives during boot.

During my research of this problem, I find many issues that seem to be related to this, but none mirror what I am going through.  My assumptions are that the HPT driver is loading before the IDE driver and taking over the slots designated IDE0 and IDE1 leaving nowhere for the on-board IDE controller to live.

LSPCI:
--------------------------------------
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0b.0 RAID bus controller: HighPoint Technologies, Inc. HPT374 (rev 07)
00:0b.1 RAID bus controller: HighPoint Technologies, Inc. HPT374 (rev 07)
00:0f.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3] (rev a3)


DMESG:
------------------------------------------------------
[    0.000000] Linux version 2.6.22-14-386 (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Sun Oct 14 22:36:54 GMT 2007 (Ubuntu 2.6.22-14.46-386)
<snip>
[   38.938559] HPT374: IDE controller at PCI slot 0000:00:0b.0
[   38.938592] HPT374: chipset revision 7
[   38.938606] HPT374: DPLL base: 48 MHz, f_CNT: 139, assuming 33 MHz PCI
[   38.942592] HPT374: using 50 MHz DPLL clock
[   38.942698] HPT374: 100% native mode on irq 5
[   38.942712]     ide2: BM-DMA at 0xb400-0xb407, BIOS settings: hde:DMA, hdf:pio
[   38.942737]     ide3: BM-DMA at 0xb408-0xb40f, BIOS settings: hdg:DMA, hdh:pio
[   38.942769] HPT374: no clock data saved by BIOS
[   39.069846] HPT374: DPLL base: 48 MHz, f_CNT: 122, assuming 33 MHz PCI
[   39.073761] HPT374: using 50 MHz DPLL clock
[   39.073873]     ide0: BM-DMA at 0xc800-0xc807, BIOS settings: hda:DMA, hdb:pio
[   39.073890]     ide1: BM-DMA at 0xc808-0xc80f, BIOS settings: hdc:DMA, hdd:pio
[   39.073903] Probing IDE interface ide2...
[   39.333502] Floppy drive(s): fd0 is 1.44M
[   39.370054] FDC 0 is a post-1991 82077
[   39.374880] hde: ST3160211AS, ATA DISK drive
[   40.043546] hde: selected mode 0x45
[   40.043765] ide2 at 0xa400-0xa407,0xa802 on irq 5
[   40.044127] Probing IDE interface ide3...
[   40.331467] hdg: ST3250620AS, ATA DISK drive
[   41.002571] hdg: selected mode 0x45
[   41.002829] ide3 at 0xac00-0xac07,0xb002 on irq 5
[   41.003183] Probing IDE interface ide0...
[   41.290492] hda: ST3250620AS, ATA DISK drive
[   41.961596] hda: selected mode 0x45
[   41.961856] ide0 at 0xb800-0xb807,0xbc02 on irq 5
[   41.962212] Probing IDE interface ide1...
[   42.249518] hdc: ST3250620AS, ATA DISK drive
[   42.920621] hdc: selected mode 0x45
[   42.920903] ide1 at 0xc000-0xc007,0xc402 on irq 5
[   42.921453] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   42.921485] VP_IDE: chipset revision 6
[   42.921487] VP_IDE: not 100% native mode: will probe irqs later
[   42.921501] VP_IDE: VIA vt8233 (rev 00) IDE UDMA100 controller on pci0000:00:11.1
[   42.921506] VP_IDE: too many IDE interfaces, no room in table
[   42.921512] VP_IDE: too many IDE interfaces, no room in table
[   42.921514] VP_IDE: neither IDE port enabled (BIOS)
<snip>


I've attached the entirety of the dmesg output.

Thanks.  Any help would be greatly appreciated.

---

### Post by fjgaude on 2007-10-28
Wow, what does fstab show:

```
sudo gedit /etc/fstab
```

How do you even get to load Gutsy, from what drive?

---

### Post by Etlaesium on 2007-10-29
When I first installed ubuntu, I installed it on the 160GB Seagate drive (which was not the boot drive).  The Fujitsu drive only has /boot on it and was obviously the boot drive.  My MoBo at the time would not boot from the SATA drives.  Wasn't a problem as long as I had the Fujitsu drive to boot from (GRUB points to the SATA).  Now, it loads from the SATA drive.  That's a good thing, but I have no access to my CD or DVD drives.

And, FSTAB isn't the problem because the IDE drives aren't even registering in /dev (IDE0 is taken over by the SATA controller).

My FSTAB:

# /etc/fstab: static file system information.
#
# <file system> 				<mount point>   <type>  	<options>       		<dump>  <pass>
proc            			   	/proc    	proc    	defaults           		0	0
# /dev/hda1
#UUID=82568137-e27e-47b3-b87a-1406a8b522db 	/		ext3    	defaults,errors=remount-ro 	0	1
/dev/hdk1				  	/		ext3		defaults,errors=remount-ro 	0	1
# /dev/hda5
#UUID=b872eb06-da22-4a31-8981-27dc8bf22099 	none 		swap    	sw              	   	0    	0
/dev/hdk5	 			   	none 		swap    	sw              	   	0    	0
/dev/hdb        				/media/cdrom0   udf,iso9660 	user,noauto     	   	0    	0
/dev/fd0        				/media/floppy0  auto		rw,user,noauto  	   	0    	0
/dev/md0					/media/raid	ext3		defaults,errors=remount-ro	0	0

---

### Post by Etlaesium on 2007-10-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/157909](https://bugs.launchpad.net/ubuntu/+bug/157909) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This bug is not resolved in 2.6.22, but an upgrade to 2.6.23 and a quick edit of the kernel config allows this problem to be worked out.  I followed the following tutorial regarding the kernel upgrade:

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

And, right before compiling the kernel, I used "xconfig" to change the following:

```

CONFIG_IDE_MAX_HWIFS=4

```
to
```

CONFIG_IDE_MAX_HWIFS=10

```
though a value of 8 probably would have sufficed.

Now, I have access to every drive on my system and each optical drive (hdb-hdd) mounts automatically when I insert a CD or DVD.  And, my RAID is fully functional.  I will remain subscribed to this thread in case anyone wants further information.

Thanks to those who have helped.

---

