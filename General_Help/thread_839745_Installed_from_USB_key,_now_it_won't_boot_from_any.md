---
title: "Installed from USB key, now it won't boot from anything else."
date: 2008-06-24
forum: General Help
---

### Post by kevlarRelic on 2008-06-24
I got a new computer the same time Hardy came out, and I decided to switch from windows cold turkey. 
The CD drive wouldn't work to install ubuntu, so I used a friends computer to put the installation files on my USB key and then booted from that and installed ubuntu.
But when I set up my comp to boot from the harddrive, it wouldn't work. So I changed it back to booting from my USB key and ubuntu started fine. 

My USB key has been stuck in my computer since then, a couple months now.  :)
Today I forgot about it and tried to start my computer with another USB drive in it. I spent three hours trying to figure out why my computer wouldn't boot until I remembered that stupid little USB drive sticking out of the back of my comp. 

I feel stupid for waiting this long to fix the problem, but I felt intimidated by linux's learning curve already, and if it wasn't broke too bad I didn't want to fix it.
 
So, I would like to boot ubuntu from my hard drive. I know enough that it's something to do with GRUB, I just don't know how to fix it. What files, if any, do I copy on to my hard drive, and where? 

Thanks for your help in this situation.

---

### Post by kevlarRelic on 2008-06-24
So, it's been an hour and this post has only gotten 6 views and no replies... It must mean my question was impossibly noobish. Could anyone just direct me to like a tutorial or something? I would be eternally greatful. Thanks again.

---

### Post by cariboo on 2008-06-24
You have a problem with grub. I have to admit once in a while I still have my problems with it.
Give this a try:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Jim

---

### Post by Dylock on 2008-06-24
So you've been running livecd off a flash drive or you installed to the flash drive? 

What error comes up when you try and boot from the hard drive?
Are you able to press ESC when prompted to get into GRUB?
If you can do that, can you post the contents of the GRUB entry?
Were there any problems during the install process?

---

### Post by kevlarRelic on 2008-06-24
Thanks for the link Cariboo907, looks like a lot of good info there!

Hey Dylock, I ran liveCD off of the flash drive only to install. Afterwards everything was installed on my hard drive, I just couldn't boot up ubuntu without my flash drive. 

No error at all comes up when I try and boot from my hd. Kinda threw me off. It just freezes at my scsi controller screen and nothing happens.

As to your other questions, I am off to restart my computer and find out. Thanks for the help!

---

### Post by VMC on 2008-06-24
Can we try and fix why your brand new computer won't boot from your cd/dvd drive.
Have you looked at your BIOS setup and change the boot up to cd/dvd first and then hard drive second.


Just so we don't cover territory twice, lets find out what kind of system you have.
From a Terminal type this:

```
sudo lshw -short
```

---

### Post by kevlarRelic on 2008-06-24
Hey Dylock, I skipped over your last question on my first read through, but there were indeed problems when I installed, related to my CD drive I believe. I would get half way through installation and then it would get an error and quit. That's why I ended up using my flash drive to install.

Perhaps the contents of the GRUB reflect that because I have the same entry pair 4 times in a row: 

Ubuntu 8.04, kernel 2.6.24-19-generic 
Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)

and a single entry of:
Ubuntu 8.04, memtest86+

I hope this information is helpful!

---

### Post by kevlarRelic on 2008-06-24
Hey VMC, my comp booted from the CD no problem, but it gave errors in the installation leading me to believe there was problems with the laser or something. I have no problems with my CD drive, just with my flash drive and booting from my hard drive. 

Here is my hard ware thingy:
H/W path                   Device      Class       Description
==============================================================
                                       system      Precision WorkStation 370
/0                                     bus         0M3849
/0/0                                   memory      64KiB BIOS
/0/400                                 processor   Intel(R) Pentium(R) 4 CPU 3.2
/0/400/700                             memory      16KiB L1 cache
/0/400/701                             memory      1MiB L2 cache
/0/400/1.1                             processor   Logical CPU
/0/400/1.2                             processor   Logical CPU
/0/1000                                memory      1GiB System Memory
/0/1000/0                              memory      512MiB DIMM DDR Synchronous 4
/0/1000/1                              memory      DIMM DDR Synchronous 400 MHz 
/0/1000/2                              memory      512MiB DIMM DDR Synchronous 4
/0/1000/3                              memory      DIMM DDR Synchronous 400 MHz 
/0/100                                 bridge      82925X/XE Memory Controller H
/0/100/1                               bridge      82925X/XE PCI Express Root Po
/0/100/1/0                             display     RV370 5B64 [FireGL V3100 (PCI
/0/100/1/0.1                           display     RV370 5B64 [FireGL V3100 (PCI
/0/100/1c                              bridge      82801FB/FBM/FR/FW/FRW (ICH6 F
/0/100/1c/0                eth0        network     NetXtreme BCM5751 Gigabit Eth
/0/100/1c.1                            bridge      82801FB/FBM/FR/FW/FRW (ICH6 F
/0/100/1d                              bus         82801FB/FBM/FR/FW/FRW (ICH6 F
/0/100/1d/1                usb1        bus         UHCI Host Controller
/0/100/1d/1/1                          generic     Kensington PocketMouse Pro
/0/100/1d.1                            bus         82801FB/FBM/FR/FW/FRW (ICH6 F
/0/100/1d.1/1              usb2        bus         UHCI Host Controller
/0/100/1d.1/1/1                        generic     DELL USB Keyboard
/0/100/1d.2                            bus         82801FB/FBM/FR/FW/FRW (ICH6 F
/0/100/1d.2/1              usb3        bus         UHCI Host Controller
/0/100/1d.3                            bus         82801FB/FBM/FR/FW/FRW (ICH6 F
/0/100/1d.3/1              usb4        bus         UHCI Host Controller
/0/100/1d.3/1/2                        generic     Inkjet color printer
/0/100/1d.7                            bus         82801FB/FBM/FR/FW/FRW (ICH6 F
/0/100/1d.7/1              usb5        bus         EHCI Host Controller
/0/100/1d.7/1/2            scsi6       generic     Cruzer Mini
/0/100/1d.7/1/2/0.0.0      /dev/sda    disk        1024MB Cruzer Mini
/0/100/1d.7/1/2/0.0.0/0    /dev/sda    disk        1024MB 
/0/100/1d.7/1/2/0.0.0/0/1  /dev/sda1   volume      976MiB Windows FAT volume
/0/100/1e                              bridge      82801 PCI Bridge
/0/100/1e/0                wlan0       network     88w8335 [Libertas] 802.11b/g 
/0/100/1e/1                scsi5       storage     ASC-39320(B) U320 w/HostRAID
/0/100/1e/1/0.0.0          /dev/sdb    disk        36GB ST336753LW
/0/100/1e/1/0.0.0/1        /dev/sdb1   volume      32GiB EXT3 volume
/0/100/1e/1/0.0.0/2        /dev/sdb2   volume      1466MiB Extended partition
/0/100/1e/1/0.0.0/2/5      /dev/sdb5   volume      1466MiB Linux swap / Solaris 
/0/100/1e/1.1              scsi7       storage     ASC-39320(B) U320 w/HostRAID
/0/100/1e/2                            multimedia  SB Audigy
/0/100/1e/2.2                          bus         SB Audigy FireWire Port
/0/100/1f                              bridge      82801FB/FR (ICH6/ICH6R) LPC I
/0/100/1f.1                scsi8       storage     82801FB/FBM/FR/FW/FRW (ICH6 F
/0/100/1f.1/0.0.0          /dev/cdrom  disk        CDRW/DVD SM-348B
/0/100/1f.1/0.1.0          /dev/sdc    disk        320GB WDC WD3200JB-00K
/0/100/1f.1/0.1.0/1        /dev/sdc1   volume      298GiB Windows NTFS volume
/0/100/1f.2                            storage     82801FR/FRW (ICH6R/ICH6RW) SA
/0/100/1f.3                            bus         82801FB/FBM/FR/FW/FRW (ICH6 F


The Cruzer Mini is the flash drive I am forced to boot from. It's interesting that it is listed as scsi6! This whole SCSI thing is new to me as well. Think it could be a problem with that sucker?

---

