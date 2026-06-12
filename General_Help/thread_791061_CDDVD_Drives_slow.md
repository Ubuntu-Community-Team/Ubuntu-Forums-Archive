---
title: "CD/DVD Drives slow"
date: 2008-05-11
forum: General Help
---

### Post by kman004 on 2008-05-11
Hey Everyone,

Just installed Ubuntu 8.04 Hardy Heron as the sole OS on my parents computer. I'm new to Linux as this is my first time installing it but I do have some basic experience from university. So far I'm really liking it and I believe this solves the ever increasing windows virus threat my parents seem to attract on a monthly basis. Got the printer and scanner working earlier, which felt really good. Anyway, blah blah blah... I have run into an issue. I would appreciate any help or suggestions.

The fix could be obvious to some, so just bare with me. I have two DVD Roms mounted (DVD reader and Writer) that are noticeably slower than they were in (cough) Windows. The writer is the faster of the two. It burns ok but slow. It plays DVD with no issue. The other seems like a write-off.. I can't really do much with it even though it does technically work. 

Some stats/tests: 
Moving files from the DVD writer to desktop: 5-7 Mb/Sec (At best)
Moving files from the DVD reader to desktop: 1 MB/Sec (At best)

Burning 10Mb file: Took 7 minutes

I'm not sure what the issue is and I've looked everywhere for the solution:

Here's some details on my setup:

username@username-Office:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=50551839-3704-4ee9-bf68-d17dd307c476 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1d4e2855-4ba0-42a8-b86b-2c9abbeefcf0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/scd0:

ATAPI CD-ROM, with removable media
	Model Number:       GENERIC DVD RW 8XMax                    
	Serial Number:      
	Firmware Revision:  140I    
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 3ms.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(can be disabled)
	Buffer size: 1024.0kB
	DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 *udma2 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=383ns  IORDY flow control=120ns

/dev/scd1:

ATAPI CD-ROM, with removable media
	Model Number:       LITEON  DVD-ROM LTD163                  
	Serial Number:      
	Firmware Revision:  GKS3    
Standards:
	Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
	Supported: CD-ROM ATAPI-2 
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(cannot be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns


--Might be a bug so tried the following as joshrobinson recommendation:
[http://ubuntuforums.org/showthread.php?p=4615284](http://ubuntuforums.org/showthread.php?p=4615284)
	sudo gedit /etc/initramfs-tools/modules
	Added lines:
		pata_atiixp
  		blacklist ata_generic
	sudo update-initramfs -u

--Might be a DMA issue
Disabled and enabled DMA on both drives. Did a reboot after each change

Tried the following:
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)
	gksudo gedit /etc/hdparm.conf
	Added lines:
		/dev/scd0 {
			dma = on
		}

		/dev/scd1 {
			dma = on
		}

I did other stuff which aren't as significant as the above. I also removed the added lines from hdparm.conf as they didn't resolve the issue.

Can anyone point me to the right direction? Thank You.

---

### Post by kman004 on 2008-05-12
bump... anyone?

---

### Post by knattlhuber on 2008-05-24
Had the same problem. This thread help me to fix it:
[http://ubuntuforums.org/showthread.php?t=739778]("http://ubuntuforums.org/showthread.php?t=739778")

---

