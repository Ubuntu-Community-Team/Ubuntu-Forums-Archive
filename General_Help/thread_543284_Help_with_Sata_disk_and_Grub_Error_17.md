---
title: "Help with Sata disk and Grub Error 17"
date: 2007-09-04
forum: General Help
---

### Post by Mariachi on 2007-09-04
I think I'm having a newbie problem :lolflag:  I'm a newbie!

The Master HD has XP, I installed a second one and installed Ubuntu. However, I have a third Sata disk where I store all my music, pics, etc and I realize that because of this disk I was getting the "Grub Error 17".

When I boot from Live Cd, it recognizes all three disks, I can even navigate through them. The thing is that when I boot normally it gives me "Grub Error 17". If I unplug the Sata disk it won't give me any errors, it displays the options to boot either from my first HD (WinXP) or my second HD (Ubuntu) but the Sata disk has to be unplugged in order for the Grub to boot correctly, and obviously the disk won't be available on any of the OS.

How can I make the Grub recognize my Sata disk and boot normally, or at least to give me the option to use it in WinXP.


Thanks for all your help!!

---

### Post by logos34 on 2007-09-04
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

Are you getting the error 17 before the grub menu screen loads, or after it tries to boot the default kernel? (I guess I should know this one--can't seem to keep it straight in my head though).  

My guess is Grub is installed on the MBR of the windows drive, pointing of course to ubuntu root on the second drive (hd1).  But for some reason when you plug in the sata drive it jumps to second place in the Bios and becomes (hd1), and the ubuntu drive shifts to third (hd2).

With the sata drive plugged in, boot the ubuntu live cd and run the following command in a terminal:

**sudo fdisk -l** (lowercase L)

Post it.

Also, if you could, run 

[B]sudo grub
find /boot/grub/stage1[/B]

what does it say?  (I'm thinking that normally it would say '(hd1,x)', but since the sata is connected might say instead '(hd2,x)'.  If it does that would confirm my hunch.  But I could be wrong).

---

### Post by Mariachi on 2007-09-05
Hi Logos34 the error happens before the menu screen loads.  It just says something like Stage 1.5 and then on the next line it says "Grub Error 17".

I will post the results a little bit later, I hope you can help me later tonight or tomorrow.

Thanks!

---

### Post by logos34 on 2007-09-05
> **Mariachi said:**
> Hi Logos34 the error happens before the menu screen loads.  It just says something like Stage 1.5 and then on the next line it says "Grub Error 17".

That's consistent with my hunch.

After you boot with the sata drive connected enter the Bios (hit F2, F12, Delete, etc.) and check if the hard disk boot order has changed.

You might try plugging the sata drive into another sata port/channel, see if that affects anything.  What motherboard is this?

sudo lspci

should give some info on the sata controller.

---

### Post by Mariachi on 2007-09-05
Here you go Sudo fdisk -l using live cd:

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4862    39053983+   7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    7  HPFS/NTFS



Here you go sudo lspci still with live cd:
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
01:01.0 Communication controller: Conexant Unknown device 2702 (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by Mariachi on 2007-09-05
Here's the fdisk -l info, booting from hard disk:

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4862    39053983+   7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris


and here's the lspci:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris
jjre@jjre-desktop:~$ 
jjre@jjre-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
01:01.0 Communication controller: Conexant Unknown device 2702 (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)


When running:
 sudo grub
find /boot/grub/stage1

It gives me this error on both live cd and hard disk:  Error 15: File not found

Thanks again for all your help!!

---

### Post by logos34 on 2007-09-05
I didn't come across any bug reports on your sata controller in launchpad.

What is the bios hard disk boot order (not the device boot order) after you plug in the sata?  Does it show up second or third?

Did you try a different sata port, as I suggested above?

You might want to read through this thread for clues to your problem:

[http://ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata&page=4](http://ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata&page=4)

> Error 15: File not found

check 

**ls /boot/grub**

if stage1 and others are indeed missing, then I'm not sure what the deal is (because you can boot fine without the sata connected.) 

You could try grub-install fix:

[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5)

---

### Post by Mariachi on 2007-09-05
Unfortunately the pc has only one SATA port.  I checked the booting sequence and first, it comes the Bios devices, then the usb.  For the drive sequence, first C: drive, floppy, then CD-ROM.


If you have any more suggestions, please let me know.

---

