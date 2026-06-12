---
title: "HD on USB3  not ready on startup of Ubuntu 14.04"
date: 2015-05-07
forum: General Help
---

### Post by Robbyx on 2015-05-07
On most occasions the USB3 HD drive is reported not to be ready on starting Ubuntu. If I skip the loading of the partitions, log into Ub gnome, pull out the usb3  cable and plug it back in the drive is recognised. Is this  a grub setting problem?

How can I ensure that the HD drive is loaded on startup?

R

---

### Post by QIII on 2015-05-07
Hello!

Could you tell us the OEM and model of your motherboard?

---

### Post by Robbyx on 2015-05-07
Gigabyte MB. S-series GA-P35C-DS3R

Some more information may help you:

The usb3 is an addon hub  plugged into a PCIE short socket.
The  hub is recognised by Ubuntu as it is shown as usb3 under lsusb.
I should have referred to the partitions not being recognised on startup instead I indicated it was the drive that was not recognised. The error messages refer to individual partitions as Ubuntu tries to load them but reports they are not ready. It did not refer to the drive as a whole or the hub.

R

---

### Post by Robbyx on 2015-05-08
Is the card showing in these reports? Do they help find the solution to the failure mount at startup. If I type mount -a, I get an error message listing the uuid's of the  partitions of the External HD with a report that they do not exist. If I pull out the cord and put it back in again the system loads the partitions automatically . Can you see the cause?

$ inxi -Fx
```

System:    Host: robins-EP35-DS3L Kernel: 3.16.0-37-generic i686 (32 bit, gcc: 4.8.2) 
           Desktop: Gnome 3.10.4 Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: EP35-DS3L version: x.x Bios: Award version: F4 date: 04/02/2008
CPU:       Dual core Intel Core2 Duo CPU E8200 (-MCP-) cache: 6144 KB flags: (lm nx pae sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 10666.7 
           Clock Speeds: 1: 2000.00 MHz 2: 2000.00 MHz
Graphics:  Card: NVIDIA G73 [GeForce 7600 GS] bus-ID: 01:00.0 
           X.Org: 1.16.0 driver: nvidia Resolution: 1920x1080@60.0hz, 1920x1080@60.0hz 
           GLX Renderer: GeForce 7600 GS/PCIe/SSE2 GLX Version: 2.1.2 NVIDIA 304.125 Direct Rendering: Yes
Audio:     Card-1: C-Media CMI8738/CMI8768 PCI Audio driver: snd_cmipci port: d000 bus-ID: 06:00.0 
           Card-2: Ensoniq ES1371 / Creative Labs CT2518 [AudioPCI-97] driver: snd_ens1371 port: d100 bus-ID: 06:02.0 
           Card-3: Intel 82801I (ICH9 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Card-4: Logitech QuickCam Pro 9000 driver: USB Audio usb-ID: 001-010 
           Sound: Advanced Linux Sound Architecture ver: k3.16.0-37-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: c000 bus-ID: 05:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 00:1d:7d:0a:01:3e
Drives:    HDD Total Size: 2314.5GB (36.8% used) 1: id: /dev/sda model: Samsung_SSD_840 size: 250.1GB temp: 0C 
           2: USB id: /dev/sdb model: Cruzer_Switch size: 64.0GB temp: 0C 3: USB id: /dev/sdd model: D3_Station size: 2000.4GB temp: 0C 
Partition: ID: / size: 13G used: 7.0G (62%) fs: ext4 ID: /home size: 34G used: 24G (75%) fs: ext4 
           ID: swap-1 size: 8.70GB used: 0.29GB (3%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 27.0C mobo: N/A gpu: 0.0:49C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 200 Uptime: 9 min Memory: 679.1/1002.4MB Runlevel: 2 Gcc sys: 4.8.2 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 


```
sudo lshw -short

```
H/W path        Device      Class       Description
===================================================
                            system      EP35-DS3L ()
/0                          bus         EP35-DS3L
/0/0                        memory      128KiB BIOS
/0/4                        processor   Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz
/0/4/a                      memory      64KiB L1 cache
/0/4/b                      memory      6MiB L2 cache
/0/4/0.1                    processor   Logical CPU
/0/4/0.2                    processor   Logical CPU
/0/1b                       memory      1GiB System Memory
/0/1b/0                     memory      DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: An
/0/1b/1                     memory      DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: An
/0/1b/2                     memory      DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: An
/0/1b/3                     memory      1GiB DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translato
/0/1                        processor   
/0/1/0.1                    processor   Logical CPU
/0/1/0.2                    processor   Logical CPU
/0/100                      bridge      82G33/G31/P35/P31 Express DRAM Controller
/0/100/1                    bridge      82G33/G31/P35/P31 Express PCI Express Root Port
/0/100/1/0                  display     G73 [GeForce 7600 GS]
/0/100/1a                   bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                 bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.2                 bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1a.7                 bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                   multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1c                   bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1c.1                 bridge      82801I (ICH9 Family) PCI Express Port 2
/0/100/1c.1/0               bus         VIA Technologies, Inc.
/0/100/1c.3                 bridge      82801I (ICH9 Family) PCI Express Port 4
/0/100/1c.3/0               storage     JMB368 IDE controller
/0/100/1c.4                 bridge      82801I (ICH9 Family) PCI Express Port 5
/0/100/1c.4/0   eth0        network     RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1d                   bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                 bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                 bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.7                 bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                   bridge      82801 PCI Bridge
/0/100/1e/0                 multimedia  CMI8738/CMI8768 PCI Audio
/0/100/1e/2                 multimedia  ES1371 / Creative Labs CT2518 [AudioPCI-97]
/0/100/1f                   bridge      82801IB (ICH9) LPC Interface Controller
/0/100/1f.2                 storage     82801IB (ICH9) 4 port SATA Controller [AHCI mode]
/0/100/1f.3                 bus         82801I (ICH9 Family) SMBus Controller
/0/2            scsi0       storage     
/0/2/0.0.0      /dev/cdrom  disk        DVD-RW  DVR-111D
/0/3            scsi7       storage     
/0/3/0.0.0      /dev/sda    disk        250GB Samsung SSD 840
/0/3/0.0.0/1    /dev/sda1   volume      8300MiB Linux swap volume
/0/3/0.0.0/2    /dev/sda2   volume      12GiB EXT4 volume
/0/3/0.0.0/3    /dev/sda3   volume      33GiB EXT4 volume
/0/3/0.0.0/4    /dev/sda4   volume      178GiB Extended partition
/0/3/0.0.0/4/5  /dev/sda5   volume      38GiB Linux filesystem partition
/0/3/0.0.0/4/6  /dev/sda6   volume      124GiB Linux filesystem partition
/0/5            scsi9       storage     
/0/5/0.0.0      /dev/sdb    disk        64GB SCSI Disk
/0/5/0.0.0/1    /dev/sdb1   volume      14GiB EXT4 volume
/0/5/0.0.0/2    /dev/sdb2   volume      44GiB EXT4 volume
/0/6            scsi10      storage     
/0/6/0.0.0      /dev/sdc    disk        MFC-5460CN
/0/6/0.0.0/0    /dev/sdc    disk        
/0/7            scsi12      storage     
/0/7/0.0.0      /dev/sdd    disk        2TB D3 Station
/0/7/0.0.0/1    /dev/sdd1   volume      300MiB Windows FAT volume
/0/7/0.0.0/2    /dev/sdd2   volume      1078GiB EXT4 volume
/0/7/0.0.0/3    /dev/sdd3   volume      413GiB EXT4 volume
/0/7/0.0.0/4    /dev/sdd4   volume      370GiB EXT4 volume
robins@robins-EP35-DS3L:~$ 

```

---

### Post by Robbyx on 2015-05-08
I tried the advice at [https://help.ubuntu.com/community/ExpressCard](https://help.ubuntu.com/community/ExpressCard)

I changed the grub line to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"

It made no difference.The Ext HD  partitions are not being recognised on startup and if after logging in  I run mount -a  I get:

[I]mount: special device UUID=13AC-9C9E does not exist
mount: special device UUID=23fcb4e3-c94e-44de-b7a9-105da58918c6 does not exist
mount: special device UUID=c99be12f-3a2d-4411-ab7c-5696167482dc does not exist
mount: special device UUID=84a9cb0b-6006-4996-8b4a-2edc07cc25c4 does not exist[/I]

pull the cable out and put it back in after I have logged in  and the partitions auto load. 

R

---

### Post by Robbyx on 2015-05-09
Is anyone ready to help me with this external HD problem? 

R

---

### Post by Robbyx on 2015-05-09
After pulling out the usb connection on the Ex HD and then replacing it, the drives are autoloaded. This is an extract from dmesg. Does this help explain why the drive is not being loaded from fstab at startup?

```
[   75.557416] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)
[   84.988052] audit_printk_skb: 272 callbacks suppressed
[   84.988055] audit: type=1400 audit(1431169494.922:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2951 comm="apparmor_parser"
[   84.988063] audit: type=1400 audit(1431169494.922:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2951 comm="apparmor_parser"
[   84.988522] audit: type=1400 audit(1431169494.922:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2951 comm="apparmor_parser"
[  135.828159] usb 1-3.1.1: reset high-speed USB device number 9 using ehci-pci
[  497.543405] perf interrupt took too long (2506 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  937.508076] usb 1-3.1.1: reset high-speed USB device number 9 using ehci-pci
[ 2177.596080] usb 10-1: USB disconnect, device number 2
[ 2177.900277] usb 10-1: new SuperSpeed USB device number 3 using xhci_hcd
[ 2177.918684] usb 10-1: New USB device found, idVendor=04e8, idProduct=6123
[ 2177.918688] usb 10-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2177.918691] usb 10-1: Product: D3 Station
[ 2177.918693] usb 10-1: Manufacturer: Samsung 
[ 2177.918696] usb 10-1: SerialNumber: 00000000011E0A49
[ 2177.919259] usb-storage 10-1:1.0: USB Mass Storage device detected
[ 2177.919336] scsi11 : usb-storage 10-1:1.0
[ 2178.164090] usb 10-1: USB disconnect, device number 3
[ 2184.712279] usb 10-1: new SuperSpeed USB device number 4 using xhci_hcd
[ 2184.729379] usb 10-1: New USB device found, idVendor=04e8, idProduct=6123
[ 2184.729383] usb 10-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2184.729386] usb 10-1: Product: D3 Station
[ 2184.729389] usb 10-1: Manufacturer: Samsung 
[ 2184.729391] usb 10-1: SerialNumber: 00000000011E0A49
[ 2184.729961] usb-storage 10-1:1.0: USB Mass Storage device detected
[ 2184.730343] scsi12 : usb-storage 10-1:1.0
[ 2185.728643] scsi 12:0:0:0: Direct-Access     Samsung  D3 Station       0200 PQ: 0 ANSI: 6
[ 2185.731414] sd 12:0:0:0: Attached scsi generic sg4 type 0
[ 2185.737049] sd 12:0:0:0: [sdd] Spinning up disk...
[ 2191.196012] .
[ 2192.144105] usb 10-1: USB disconnect, device number 4
[ 2192.200013] .ready
[ 2192.200092] sd 12:0:0:0: [sdd] READ CAPACITY failed
[ 2192.200095] sd 12:0:0:0: [sdd]  
[ 2192.200098] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 2192.200100] sd 12:0:0:0: [sdd] Sense not available.
[ 2192.200117] sd 12:0:0:0: [sdd] Write Protect is off
[ 2192.200121] sd 12:0:0:0: [sdd] Mode Sense: 2e 2e 2f 2e
[ 2192.200138] sd 12:0:0:0: [sdd] No Caching mode page found
[ 2192.200142] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[ 2192.200378] sd 12:0:0:0: [sdd] READ CAPACITY failed
[ 2192.200381] sd 12:0:0:0: [sdd]  
[ 2192.200382] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 2192.200385] sd 12:0:0:0: [sdd] Sense not available.
[ 2192.200408] sd 12:0:0:0: [sdd] Attached SCSI disk
[ 2192.908291] usb 10-1: new SuperSpeed USB device number 5 using xhci_hcd
[ 2192.925395] usb 10-1: New USB device found, idVendor=04e8, idProduct=6123
[ 2192.925399] usb 10-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2192.925402] usb 10-1: Product: D3 Station
[ 2192.925404] usb 10-1: Manufacturer: Samsung 
[ 2192.925407] usb 10-1: SerialNumber: 00000000011E0A49
[ 2192.925965] usb-storage 10-1:1.0: USB Mass Storage device detected
[ 2192.926040] scsi13 : usb-storage 10-1:1.0
[ 2193.924624] scsi 13:0:0:0: Direct-Access     Samsung  D3 Station       0200 PQ: 0 ANSI: 6
[ 2193.925035] sd 13:0:0:0: Attached scsi generic sg4 type 0
[ 2193.930192] sd 13:0:0:0: [sdd] 3907029167 512-byte logical blocks: (2.00 TB/1.81 TiB)
[ 2193.930880] sd 13:0:0:0: [sdd] Write Protect is off
[ 2193.930885] sd 13:0:0:0: [sdd] Mode Sense: 2b 00 10 08
[ 2193.931983] sd 13:0:0:0: [sdd] Write cache: enabled, read cache: enabled, supports DPO and FUA
[ 2193.950368]  sdd: sdd1 sdd2 sdd3 sdd4
[ 2193.953670] sd 13:0:0:0: [sdd] Attached SCSI disk
[ 2194.515569] FAT-fs (sdd1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[ 2194.527345] EXT4-fs (sdd3): mounted filesystem with ordered data mode. Opts: (null)
[ 2194.585050] EXT4-fs (sdd4): mounted filesystem with ordered data mode. Opts: (null)
[ 2194.827464] EXT4-fs (sdd2): mounted filesystem with ordered data mode. Opts: (null)

```

---

### Post by QIII on 2015-05-09
Sorry.  "Real Life" got in the way of getting back to you.

When I first saw "Gigabyte" I thought of one possible solution until you said your USB 3.0 is on a PCIe card.  So that possibility is out.

Is your drive powered externally, or is it taking power from the USB hub?

---

### Post by Robbyx on 2015-05-09
Powered externally.

---

### Post by QIII on 2015-05-09
OK.  Well, that shoots another possibility down.

Start up your machine.  Don't unplug and then replug the device.  Just have it plugged in when you boot and leave it alone.

Issue the following in the terminal and post the results:

```
sudo fdisk -l
```

and

```
sudo lsblk -io NAME,TYPE,SIZE,MOUNTPOINT,FSTYPE,MODEL
```

I don't remember for sure if the second will work on Ubuntu.  It should. I think ...  :)

---

### Post by Robbyx on 2015-05-09
```
 sudo fdisk -l
[sudo] password for robins: 

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00083267

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    17000447     8499200   82  Linux swap / Solaris
/dev/sdb2   *    17000448    43010047    13004800   83  Linux
/dev/sdb3        43010048   114014207    35502080   83  Linux
/dev/sdb4       114016254   488396799   187190273    5  Extended
/dev/sdb5       114016256   193888255    39936000   83  Linux
/dev/sdb6       193890304   455014399   130562048   83  Linux

Disk /dev/sdc: 64.0 GB, 64016220160 bytes
255 heads, 63 sectors/track, 7782 cylinders, total 125031680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cd66b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048    30722047    15360000   83  Linux
/dev/sdc2        30722048   125030399    47154176   83  Linux
robins@robins-EP35-DS3L:~$ sudo lsblk -io NAME,TYPE,SIZE,MOUNTPOINT,FSTYPE,MODEL
NAME   TYPE   SIZE MOUNTPOINT                                         FSTYPE MODEL
sdb    disk 232.9G                                                           Samsung SSD 840 
|-sdb1 part   8.1G [SWAP]                                             swap   
|-sdb2 part  12.4G /                                                  ext4   
|-sdb3 part  33.9G /home                                              ext4   
|-sdb4 part     1K                                                           
|-sdb5 part  38.1G /media/mydocs                                      ext4   
`-sdb6 part 124.5G /media/audio_visual                                ext4   
sdc    disk  59.6G                                                           Cruzer Switch   
|-sdc1 part  14.7G /media/robins/4a123674-ac85-4d66-bfd7-3b12e330b961 ext4   
`-sdc2 part    45G /media/robins/8f79ed83-bf2f-4d5a-b7ce-11a8d8d66cbc ext4   
sr0    rom   1024M                                                           DVD-RW  DVR-111D

```

NB
sdc is a memory stick. The ex. HD is not listed above.

---

### Post by QIII on 2015-05-10
Thanks.  So clearly not there to be seen by the OS.

Is the disk recognized by your UEFI/BIOS if it is plugged in when you power on?

---

### Post by Robbyx on 2015-05-11
My bios can only shows  ide drives it has no place to show other types of drives. . Even if it was being recognised I could not tell from the bios. However because of the wording of the error messages when Ubuntu tries to load the usb partitions I would assume that it is not being recognised. Is there a way of forcing Ubuntu to see the usb card other than unplugging and then connecting the power to the drive,  because then the partitions are mounted by Ubuntu.

---

### Post by Robbyx on 2015-05-11
The External HD loads perfectly when I move the cable from the USB3 card to one of the USB2 ports. I have just turned off the machine, moved the cable to the USB2 socket, restarted and logged in. The disk  was mounted correctly without any error messages.

---

### Post by QIII on 2015-05-12
Look through your BIOS settings.  Is there one for IOMMU?

---

### Post by Robbyx on 2015-05-12
There is no IOMMU

---

### Post by QIII on 2015-05-12
OK. 

So, 

1.  No IOMMU setting -- which causes problems on some newer Gigabyte mobos.

2.  Does not automount at startup when plugged into USB 3.0 port provided by add-on PCIe adapter.

3.  Mounts when plugged in after startup on USB 3.0 port provided by add-on PCIe adapter.

4.  Automounts at startup when plugged in to an available mobo USB 2.0 port.  That was a good diagnostic move, by the way!

Is that where we are now?  

(Old men with grey hair sometimes have to jot things down. We also sometimes forget why we are at the grocery store when our wives have sent us out for a gallon of milk. ;) )

It looks like we need to explore why this won't work using the PCIe adapter -- and I don't have a ready answer.

Could you tell us more about that adapter?

---

### Post by Robbyx on 2015-05-12
If I was asked to get a gallon of milk I too would forget why I was there, but in my case I hope the reason would be  that I am vegan.

You summary is correct.

Here is the product link on Ebay. 

[http://is.gd/zhYFMb](http://is.gd/zhYFMb)

R

---

### Post by QIII on 2015-05-12
Thanks.  Might have to dig to see if I can come up with some tech specs on that.

Here's my suspicion, but it might take some experimentation and research so I can't say for sure right now:

Things like PCIe SATA raid adapters have firmware that starts while the motherboard is starting up that can signal to the mobo that they exist and have disks attached.  Some PCIe SSDs also have firmware to signal to some more recent boards that they are bootable.  (I happen to be doing some research and testing on using "bootable" PCIe SSDs as OS disks in Linux -- something Windows users with certain very recent Intel boards already enjoy!  I hope to be able to blog about that in a few weeks, but real life often cuts into my play time.)

What I suspect here, but I don't know, is that the combination of your older (or designed without USB 3.0 support) board and the PCIe USB 3.0 adapter means that the motherboard never knows about its existence until the adapter signals an event (like plugging in the drive) and makes the mobo aware of itself.  Then, the mobo lets the running OS know and your drive is mounted.

The USB 2.0 works without a hitch because your board is designed in such a way that it knows about drives attached to USB 2.0, but not USB 3.0 through PCIe.

I haven't encountered anything like this since my mobos all have on-board USB 3.0 support.

I am wondering if an eSATA adapter would work just fine.

It would be good for both of us to do some google-sleuthing to find out if that is the case and what can be done about it.  I'm sure you are not the only user on UF with this sort of issue.  I'm sure there are also other Ubuntu (Linux in general) users.

Or, perhaps some other kind UF user will step in and say "Oh, yeah!  That's easy!"

---

### Post by Vladlenin5000 on 2015-05-12
The only instance where I used an add-on USB 3.0 card, this one
```
02:00.0 USB controller: Renesas Technology Corp. uPD720201 USB 3.0 Host Controller (rev 03)
```
was also in a 2012 Gigabyte G41M-Combo and all connected devices are correctly mounted at startup. Cannot boot from it though.

---

### Post by Robbyx on 2015-05-15
Two ideas flow from what we have discussed:

Should I be updating my mob?. Although my current one is now old I wonder if I would see any benefit from upgrading, as apart from watching the occasional video all my other activities are emails, browsing, and word processing. I would have thought I would gain more from a new video card mine is a Geforce 7600GS.

The other is to look for an Esata  adapter. There are a few price aceptable ones on ebay but they seem to go in the wrong direction from  USB 3 to Esata. [http://www.ebay.co.uk/itm/Portable-eSATA-to-USB-3-0-External-Adapter-Converter-Black-with-Indicator-Light-/201171829342?pt=LH_DefaultDomain_3&hash=item2ed6c6825e](http://www.ebay.co.uk/itm/Portable-eSATA-to-USB-3-0-External-Adapter-Converter-Black-with-Indicator-Light-/201171829342?pt=LH_DefaultDomain_3&hash=item2ed6c6825e)

I have asked the supplier if he hasn't made a mistake in the description.

R

---

### Post by Robbyx on 2015-05-18
Am I going down the right route to sort my problem?

R

> **Robbyx said:**
> Two ideas flow from what we have discussed:

Should I be updating my mob?. Although my current one is now old I wonder if I would see any benefit from upgrading, as apart from watching the occasional video all my other activities are emails, browsing, and word processing. I would have thought I would gain more from a new video card mine is a Geforce 7600GS.

The other is to look for an Esata  adapter. There are a few price acceptable ones on ebay but they seem to go in the wrong direction from  USB 3 to Esata. [http://www.ebay.co.uk/itm/Portable-eSATA-to-USB-3-0-External-Adapter-Converter-Black-with-Indicator-Light-/201171829342?pt=LH_DefaultDomain_3&hash=item2ed6c6825e](http://www.ebay.co.uk/itm/Portable-eSATA-to-USB-3-0-External-Adapter-Converter-Black-with-Indicator-Light-/201171829342?pt=LH_DefaultDomain_3&hash=item2ed6c6825e)

I have asked the supplier if he hasn't made a mistake in the description.

R

---

