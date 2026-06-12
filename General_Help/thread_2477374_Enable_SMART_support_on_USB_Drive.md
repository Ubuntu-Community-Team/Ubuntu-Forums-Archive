---
title: "Enable SMART support on USB Drive?"
date: 2022-07-22
forum: General Help
---

### Post by rsteinmetz70112 on 2022-07-22
I have an external USB drive I used for backups I ran smartctl on it and got the following:

```
# smartctl --all -d scsi -s /dev/sde
User Capacity:        4,000,787,029,504 bytes [4.00 TB]
Logical block size:   512 bytes
Physical block size:  4096 bytes
Logical Unit id:      0x5000000000000001
Serial number:        00000000NABZ0E5B
Device type:          disk
Local Time is:        Fri Jul 22 17:06:47 2022 EDT
SMART support is:     Available - device has SMART capability.
SMART support is:     Disabled
Temperature Warning:  Disabled or Not Supported


=== START OF ENABLE/DISABLE COMMANDS SECTION ===
Informational Exceptions (SMART) disabled
Temperature warning disabled


=== START OF READ SMART DATA SECTION ===
SMART Health Status: OK
Current Drive Temperature:     0 C
Drive Trip Temperature:        0 C


Error Counter logging not supported


Device does not support Self Test logging

```
According to this the drive has SMART support, but it's apparently turned off.
I've tried adding --smart=on to my smartctl commands but I either get and error or nothing else happens.
also using "-d ata" which doesn't work or "-d sat,auto" which give the same output as above.
the drive is a Seagate Basic

OK I found this on smartmontools [https://www.smartmontools.org/ticket/971](https://www.smartmontools.org/ticket/971)
It appears to be an issue with some drives.
There is more information here [https://www.smartmontools.org/wiki/SAT-with-UAS-Linux](https://www.smartmontools.org/wiki/SAT-with-UAS-Linux)

---

### Post by TheFu on 2022-07-23
If SMART is off, that usually needs to be enabled in the BIOS for the entire system.  If other drives have the expected SMART data, then smartctl has some different device types which you can try.  This is related to the controller, since any popular HDD/SSD will have SMART capabilities. The USGovt mandated it decades ago, so if a storage provider ever wanted to sell to the USGovt, SMART needed to be possible.

Some controllers aren't supported. There isn't much we can do about those, except to avoid them.

A few of my USB connected backup disks require a "-d sat" option for all SMART commands.  There is an auto setting, but it seems to work to determine the correct option that we need to add only. The manpage has more on this.

---

### Post by rsteinmetz70112 on 2022-07-25
OK All of my SATA drives work just fine. I have one USB drive which has this problem. Nothing I've tried enables SMART support, including the -d sat or -d ata whihc both fail with an error -d scsi does return some information.  

I did some more research. It appears that smartctl is disabled on Seagate USB drives because a lot of their USB controllers have been broken.

---

### Post by sudodus on 2022-07-25
What kind of USB drive is it? I guess not a SATA drive or NVMe drive in an adapter or box, but a 'closed box', difficult to open. In that case it could be difficult to make SMART work. But at least you should be able to check the file system (and if necessary mark bad sectors as bad).

---

### Post by rsteinmetz70112 on 2022-07-25
The drive is a Seagate Basic USB 3 4TB drive it is powered by the USB port. It is a spinning drive I found a Youtube video on how to disassemble the 5TB version of the drive with a guitar pick. The drive appears to be a 2.5" sata drive with a small add on USB interface..

---

### Post by TheFu on 2022-07-25
USB powered spinning disks, if they work, usually are very slow.  These days, if I need a portable USB drive with USB-only power, then I'd buy a cheap m.2 or 2.5inch SATA SSD to put into a $10-$20 USB3 enclosure.

For backups, I want a separately powered USB drive/dock/enclosure with at least a USB3 interface - not that any spinning disk can come close to that speed, but because the bus speed means that slightly better chips and interfaces are used than with USB2.

I do have a few legacy USB3 external storage HDDs that are powered over USB. They are much faster than USB2, but nowhere near what the HDD provides when used internally. Those are used if I'm traveling for extended periods and a few 64G microSD cards aren't enough storage for backups during travel.  I don't have any working SSD-based external storage devices. The SSDs in those have all died, but they were cheap, not from any reputable vendor.

---

### Post by rsteinmetz70112 on 2022-07-26
This drive is a USB 3, I don't think a USB 2 port would have enough power. I use it as a secondary remote backup. It operates via a series of crontabs to pull data from other computers usually late at night so I'm not too concerned about speed.

---

### Post by rsteinmetz70112 on 2022-08-03
OK I've discovered that Seagate has a version of it's Seatools which works with Linux. I haven't tried it yet but it appears to have the ability to access SMARTTOOLS

---

