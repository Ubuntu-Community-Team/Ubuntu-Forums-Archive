---
title: "External HDD with UAS driver checking disk health"
date: 2024-05-26
forum: General Help
---

### Post by JamButty on 2024-05-26
Short-form: my external HDD cannot be checked for corruption.
The documentation on checking the problem and it's solutions are over my head.

Long-form:
To my great shock, I just found out that my external HDD, a four year old Seagate 2TB expansion, which I had always assumed was being continually checked by SMART, is not. As it contains a lifetime of texts, music collection, art, photographs etc. this is not so wonderful. I do backups routinely but if that external drive has become in any way corrupted, then the backups are just backups of corrupted data. Lack of SMART access to it is shown in DISKS gui - "SMART data and self-tests" from the menu is active for the internal HDDs but greyed out for the external one.
I have tried going through the official texts for this:
[https://www.smartmontools.org/wiki/Supported_USB-Devices](https://www.smartmontools.org/wiki/Supported_USB-Devices)
and
[https://www.smartmontools.org/wiki/SAT-with-UAS-Linux](https://www.smartmontools.org/wiki/SAT-with-UAS-Linux).
I do not understand most of that, but have determined it seems to be one of the problem devices using UAS:

```
lsusb -t 
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/10p, 480M
    |__ Port 3: Dev 7, If 0, Class=Mass Storage, Driver=uas, 480M
    
```

Tried to confirm with suggested error invocation via smartctl and hdparm that the NO_ATA_1X flag is likely in effect. The smartctl created the same error as shown in the documentation, but the hdparm did not, so I have no idea what that means (HDD has two partitions which became /dev/sdd1 and /dev/sdd2):

```
$ sudo smartctl -d sat -a /dev/sdd1
[sudo] password for fred: 
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-6.5.0-35-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, www.smartmontools.org

Read Device Identity failed: scsi error unsupported field in scsi command

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
$ sudo smartctl -d sat -a /dev/sdd2
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-6.5.0-35-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, www.smartmontools.org

Read Device Identity failed: scsi error unsupported field in scsi command

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
$ sudo smartctl -d sat -T permissive -a /dev/sdd1
[sudo] password for fred: 
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-6.5.0-35-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, www.smartmontools.org

Read Device Identity failed: scsi error unsupported field in scsi command

=== START OF INFORMATION SECTION ===
Device Model:     [No Information Found]
Serial Number:    [No Information Found]
Firmware Version: [No Information Found]
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   [No Information Found]
Local Time is:    Sat May 25 21:12:33 2024 PDT
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 82-83 don't show if SMART supported.
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 85-87 don't show if SMART is enabled.
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

$ sudo smartctl -d sat -T permissive -a /dev/sdd2
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-6.5.0-35-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, www.smartmontools.org

Read Device Identity failed: scsi error unsupported field in scsi command

=== START OF INFORMATION SECTION ===
Device Model:     [No Information Found]
Serial Number:    [No Information Found]
Firmware Version: [No Information Found]
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   [No Information Found]
Local Time is:    Sat May 25 21:13:30 2024 PDT
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 82-83 don't show if SMART supported.
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 85-87 don't show if SMART is enabled.
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

$ sudo hdparm -I /dev/sdd1

/dev/sdd1:

ATA device, with non-removable media
Standards:
    Likely used: 1
Configuration:
    Logical        max    current
    cylinders    0    0
    heads        0    0
    sectors/track    0    0
    --
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:           0 MBytes
    device size with M = 1000*1000:           0 MBytes 
    cache/buffer size  = unknown
Capabilities:
    IORDY not likely
    Cannot perform double-word IO
    R/W multiple sector transfer: not supported
    DMA: not supported
    PIO: pio0 
$ sudo hdparm -I /dev/sdd2

/dev/sdd2:

ATA device, with non-removable media
Standards:
    Likely used: 1
Configuration:
    Logical        max    current
    cylinders    0    0
    heads        0    0
    sectors/track    0    0
    --
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:           0 MBytes
    device size with M = 1000*1000:           0 MBytes 
    cache/buffer size  = unknown
Capabilities:
    IORDY not likely
    Cannot perform double-word IO
    R/W multiple sector transfer: not supported
    DMA: not supported
    PIO: pio0 

``` 
   
The "permanent flag settings" solution section I understand nothing about.
The "temporary settings" section looks simpler, but I don't understand how it addresses that particular device (those particular partitions) as there is nothing specifying a device. But I can try it if it will allow me to check the health of that drive. The temp solution is:

```
# cat /sys/module/usb_storage/parameters/quirks 

# echo "0x0bc2:0x231a:u" > /sys/module/usb_storage/parameters/quirks 
# cat /sys/module/usb_storage/parameters/quirks 
0x0bc2:0x231a:u

```

So my questions are:
1. Are these universal literal commands or is the "0x0bc2:0x231a:u" value given just an example?
2. This is supposed to allow me to use smartctl until the next reboot. But smartctl is not SMART (when I started looking into this, smartctl/smartmontools was not even installed). Should this solution mean that I would also be able to use the DISKS gui to check the disk health?

thank you.

---

### Post by TheFu on 2024-05-26
Are you sure you need to use the  **-d sat** option?  Sometimes it isn't needed with USB.

a) Seagate 2TB HDDs have a poor reliability record. Some models failed 4x more often then the competition.  
b) I owned 2 Seagate 2TB HDDs. One failed at 11 months and the other at 13 months.  It was a happy day when the 2nd one failed. I haven't purchased anything from Seagate ever since.  Seagate management LIED to customers in the early 2000s about design flaws of the HDDs over 750GB in size. I used to seek out seagate because they had a great reputation for reliability and fixing issues. Gave them 2 chances, which they blew.  Fool me once .... 
c) SMART requires the motherboard BIOS to be enabled for it AND the disk controller to provide it. If either one of those isn't enabled (or unsupported), then SMART won't work.
d) SMART will only provide hints that a drive may be failing 78% of the time. 22% of the time, there is nothing in the SMART data to show anything wrong.
e) If the USB controller is preventing SMART from working, you can remove the HDD from the enclosure and connect it to a SATA/SAS port directly.  I can't think of any SATA/SAS disks that don't have SMART capability since the early 1990s with the USGovt mandated some way to test disks for potential failures. Not all USB controllers are good.

If the USB controller is in the way of getting SMART data, assume anything coming from it is bogus.

SMART is just about the HDD hardware, not the file systems, partitions, or other logical aspects of the HDD.  There are other tools for those which are dependent on the partition type and file system type(s).  **fsck** is the normal method used to verify native Linux file systems.  BTRFS and ZFS have their own tools which must be used.  When using fsck, the file system cannot be mounted/active.

Once SMART is enabled in the BIOS, it remains enabled.  I cannot think of any reason NOT to have it enabled. None.
I get SMART error notifications via email. I have no idea how other people get those notifications if they don't have an MTA setup on their systems.  I always have an MTA on my systems. Always.  This way, emails know how to be forwarded to my mail server so I'll actually see them.

SMART doesn't work well with NVMe SSDs. There just isn't much data provided.  SATA-SSDs report in a similar table to what SATA HDDs report.

USB storage has all sorts of issues.  I've seen my share over the decades.  I only use USB storage for backup storage, never primary storage.  I've been burned too many times.  External storage that hold the primary copy of data is either eSATA connected or I use Infiniband connectors.  I got a good deal on some infiniband connectors, so most people would find eSATA the better option.  eSATA is 100% SATA and connects at SATA speeds supporting the full SATA protocol.  There used to be relatively cheap eSATA 4-drive external enclosures that supported hot-swap.  Don't know if those still exist or how well they work with Linux these days.  I have an Addonics array and a MediaSonic array.  The Addonics company seems to have learned they could triple their prices and lean towards much more expensive hardware than what I have.  The MediaSonic array uses virtual buttons which suck. After a power failure that is too long (more than 1-2 minutes), the array will not restart when power returns, until someone physically touches the power switch.  Also, if the computer it is connected into is off, that's also considered a power failure.  I am not amused by either of these situations.  It isn't THAT big of an issue. I have a few UPS devices to make trivial power spikes or an outage less than 45 minutes a non-issue, but about once every 2-3 years, there is a 4-6 hour power outage here.  If they happen in the middle of the night - fine.  It is the weekday, all-day, outages that are a problem.

I run short smart tests weekly and monthly, I do a long smart test instead.  The reports for all the storage here is retained at least 6 months.  It is the changes over time where SMART data is most helpful.  Last month, I posted an example of a quality HDD that failed over a few weeks. I had the SMART reports which showed it happen, slowly, until it stopped working.  I'd already started the RMA process before that time.  Amazing how long RAM can take - nearly a month after their internal screwups.  They actually "lost" the drive for 7 days from when they claimed it had been shipped, but the shipping company didn't get it!

---

### Post by oldfred on 2024-05-26
I have not had a HDD in an external USB adapter.
The one I had years ago SATA to USB, worked well for an old SSD, but was USB powered and would not spin up the old HDD.

But when researching for USB to M.2 adapters found this:
Want for better support of a drive on a USB port and faster transfer
UASP (USB Attached SCSI Protocol)

The standard has been around for years with USB3, it turns out, but both hardware, operating system, and external device must support it.

Are you using a USB3 port?
Does drive specs mention USB3 with UASP support?

---

### Post by JamButty on 2024-05-26
Thanks TheFu and oldfred for input. I will study it and see what I can understand.
"Are you sure you need to use the  **-d sat** option?" 
Sorry if I gave the impression I had any idea what I am doing. I don't. I just groped blindly through those two docs I listed and copy pasted the code that seemed relevant changing the device references. I have never used smartctl before and have no idea what it is doing or what the parameters indicate. I had heard of SMART before and understood its scans were automatic and thought no further of it. I have received error notices from it in the past from the oldest internal HDD.
At this point, as far as I understand both your comments, it is looking like the clearest path is to chuck that Seagate hdd altogether and look for reliable alternatives. I liked the idea of the easy portability of the external drive but it does not seem to be worth the further risk. Not sure if my old tower (2014) has the capacity for another internal HDD - I have two in it now - but I will look into that also. My focus is archival - I'm not doing anything that requires warp-speed response times, so reliability it the issue.

"Are you using a USB3 port?
Does drive specs mention USB3 with UASP support?" Don't know yet about UASP support. System supports USB3
```
$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 003 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 0424:2412 Microchip Technology, Inc. (formerly SMSC) 
Bus 003 Device 002: ID 0bc2:231a Seagate RSS LLC Expansion Portable
Bus 003 Device 007: ID 0cf3:0036 Qualcomm Atheros Communications AR9462 Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Tower has two blue-tabbed USB ports marked "SS" USB3 ports and three black-tabbed USB2 ports. This confuses a bit as the lsusb output references three USB2 devices but only one USB3.

I will study further.

---

### Post by oldfred on 2024-05-26
This may show more info, not sure what it shows on your Seagate.
lsusb
Details on one port, first number is bus, second is device:
lsusb -v -s X:Y

Or 
lsusb -v -s 3:2

---

### Post by TheFu on 2024-05-27
Sometimes _-d SAT_ **is** required and it is usually required with USB connections, but not allows.  I asked only because I've seen it no used and used - just depends on the USB controller and which USB storage driver is being used. There are at least 2 types of USB-storage drivers.  Had a system from 2010 that only worked with 1. It was a USB3 hub bug that needed a firmware update, but since their firmware update was only possible from a Win7 system with a USB3 port, I wasn't able to apply it.  I had Win7 on hardware, but it only had USB2 ports.  sigh.  None of my friends had MS-Windows. ... eventually, the Linux drivers were updated to negate the chip/driver bug.

---

### Post by JamButty on 2024-05-29
"you can remove the HDD from the enclosure and connect it to a SATA/SAS port directly."
It is a sealed unit with only the port opening. Destroying my enclosure on the hope I could figure out how to attach it to a SATA port would be a last-ditch option. Even so I would probably destroy the HDD in the process.

Could not find any reference to UASP support in documentation on that drive.

The question I had about whether the quirks file flag value the documentation described may be moot as my system will not allow me to write to that file with or without root priv.
Tried writing that value, then writing just a null value and it was rejected both times.
Why can't I write to that file?
```
cat /sys/module/usb_storage/parameters/quirks

$ echo "0x0bc2:0x231a:u" > /sys/module/usb_storage/parameters/quirks
bash: /sys/module/usb_storage/parameters/quirks: Permission denied
$ sudo echo "0x0bc2:0x231a:u" > /sys/module/usb_storage/parameters/quirks
bash: /sys/module/usb_storage/parameters/quirks: Permission denied
$ ls /sys/module/usb_storage/parameters/quirks
/sys/module/usb_storage/parameters/quirks
$ cat /sys/module/usb_storage/parameters/quirks

$ sudo echo "" > /sys/module/usb_storage/parameters/quirks
bash: /sys/module/usb_storage/parameters/quirks: Permission denied
```

The lsusb/usb3 confusion is ok - for whatever reason system reports on all the usb2 ports (all unused), but only on usb3 ports when they are in use. Output of sudo lshw -class disk -class storage lists bus 4 dev 1 when seagate is plugged into one of them and bus4 dev 2 when it is plugged into the other, but lsusb shows only the port currently in use
```
$ sudo lshw -class disk -class storage
  *-usb
       description: Mass storage device
       product: Expansion
       vendor: Seagate
       physical id: 2
       bus info: usb@4:2
       logical name: scsi5
       version: 7.10
       serial: NAARB49M
       capabilities: usb-3.00 scsi
       configuration: driver=uas maxpower=896mA speed=5000Mbit/s

---swap ports----

$ sudo lshw -class disk -class storage
  *-usb
       description: Mass storage device
       product: Expansion
       vendor: Seagate
       physical id: 1
       bus info: usb@4:1
       logical name: scsi5
       version: 7.10
       serial: NAARB49M
       capabilities: usb-3.00 scsi
       configuration: driver=uas maxpower=896mA speed=5000Mbit/s
```

Seagate has their own diagnostics app that I tried. As far as I can tell, it just repackages SMART data. It could not diagnose the external HDD either.
On the plus side that drive looked ok under fsck.
```
$ sudo fsck /dev/sdc1
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
Backups2: clean, 2304/19202048 files, 30990883/76800000 blocks
$ sudo fsck /dev/sdc2
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
MoMuse: clean, 78689/102899712 files, 215264546/411578368 blocks
```


I still would like to try the "quirks" workaround that the official documentation advised if anyone can explain both whether that value would be kosher and why I can't write to it with CAT.

---

