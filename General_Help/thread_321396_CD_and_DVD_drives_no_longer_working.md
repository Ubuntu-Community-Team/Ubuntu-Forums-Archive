---
title: "CD and DVD drives no longer working"
date: 2006-12-18
forum: General Help
---

### Post by briguyd on 2006-12-18
I was running Dapper fine until a few weeks ago. My computer died. After a while of switching out cables and stuff for the hard drives and stuff, I removed the extra RAM I had installed and got it working. I then booted back into my existing OS and upgraded to Edgy. Now both me disc drives are not working. They worked under Dapper, and my floppy drive works under Edgy, but the CD-RW an d DVD-ROM drive no longer automatically mount when I put something in one of them. I've tried doing some messing around in /etc/fstab, but have had no luck so far. 

Can anyone please help me?

---

### Post by briguyd on 2006-12-19
Anyone?

Which thingy in /dev usually is a CD/DVD drive? I see hde, hde1, hdf, hdf1, sda, sda1, sda2, and sda5. Any of those look likely?

---

### Post by taurus on 2006-12-19
You can look at /var/log/messages or run this from a terminal, hitting space for the next 24 lines...

Applications -> Accessories -> Terminal
```
dmesg | more
```

---

### Post by antealin on 2007-02-18
I got the same error, but I haven't needed to use my dvd-device yet.

The output from dmesg is full of these messages:

```

[17256397.848000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x0
[17256397.848000] ata2: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
[17256427.848000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x0
[17256427.848000] ata2: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
[17256427.848000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
[17256427.848000] sr: Current [descriptor]: sense key: Aborted Command
[17256427.848000]     Additional sense: Scsi parity error
[17256437.848000] ata2: command 0xa0 timeout, stat 0xd0 host_stat 0x0
[17256437.848000] ata2: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
[17256437.864000] sr 1:0:0:0: ioctl_internal_command return code = 8000002
[17256437.864000]    : Current [descriptor]: sense key: Aborted Command
[17256437.864000]     Additional sense: Scsi parity error

```


Any ideas?
The problems came up when I upgraded from Dapper to Edgy.

---

