---
title: "proper way to set hard drive spindown to 1 minute every boot?"
date: 2007-12-08
forum: General Help
---

### Post by gnychis on 2007-12-08
Hi all,

what's the proper way in ubuntu to set specific devices, like /dev/sdb and /dev/sdc to spindown after being idle every boot?

Thanks!
George

---

### Post by narsaw on 2007-12-26
you are looking for hdparm.

sudo apt-get install hdparm to install the software. Then edit /etc/hdparm.conf to add your devices.

Mine looks like
.
.
.
/dev/hda {
        spindown_time = 240
}

/dev/hdb {
        spindown_time = 240
}

/dev/sda {
        spindown_time = 240
}
/dev/sdb {
        spindown_time = 240
}

.
.
.

---

### Post by mdurham on 2008-01-02
> **narsaw said:**
> you are looking for hdparm.

sudo apt-get install hdparm to install the software. Then edit /etc/hdparm.conf to add your devices.

Mine looks like
.
.
.
/dev/hda {
        spindown_time = 240
}

/dev/hdb {
        spindown_time = 240
}

/dev/sda {
        spindown_time = 240
}
/dev/sdb {
        spindown_time = 240
}

.
.
.

what units are the numbers in?

---

### Post by sonofusion82 on 2008-01-02
It is a rather unusually scale as described in the man pages for hdparm

> The encoding of the timeout value is somewhat peculiar. A value of zero means "timeouts are disabled": the device will not automatically enter standby mode. Values from 1 to 240 specify multiples of 5 seconds, yielding timeouts from 5 seconds to 20 minutes. Values from 241 to 251 specify from 1 to 11 units of 30 minutes, yielding timeouts from 30 minutes to 5.5 hours. A value of 252 signifies a timeout of 21 minutes. A value of 253 sets a vendor-defined timeout period between 8 and 12 hours, and the value 254 is reserved. 255 is interpreted as 21 minutes plus 15 seconds

So, narsaw's 240 means 240 * 5 seconds = 1200 seconds => 20 mins

---

### Post by ymo on 2008-01-02
> **mdurham said:**
> what units are the numbers in?
$ man hdparm

In summary:

0 = disabled
1..240 = multiples of 5 seconds (5 seconds to 20 minutes)
241..251 = 1..11 x 30 mins
252 = 21 mins
253 = vendor defined (8..12 hours)
254 = reserved
255 = 21 mins + 15 secs

Edit: Not quick enough :-)

---

### Post by gnychis on 2008-01-08
to start out, I want to set all of the spindown times to 0 and APM to 254... but I get errors.  Here is my /etc/hdparm.conf:
```

# -q be quiet
#quiet 

/dev/sda {
apm = 254
spindown_time = 0
}

/dev/sdb {
apm = 254
spindown_time = 0
}

/dev/sdc {
apm = 254
spindown_time = 0
}

/dev/sdd {
apm = 254
spindown_time = 0
}

/dev/sde {
apm = 254
spindown_time = 0
}

```

Then i restart hdparm:
```

root@monster:~# /etc/init.d/hdparm restart
 * Setting disc parameters...                                                                                                                                                                                                                  
/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
 setting standby to 0 (off)

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
 setting standby to 0 (off)

/dev/sdc:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
 setting standby to 0 (off)

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
 setting standby to 0 (off)

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
 setting standby to 0 (off)

```

What are the HDIO_DRIVE_CMD input/output errors?

---

### Post by dcstar on 2008-01-08
> **gnychis said:**
> to start out, I want to set all of the spindown times to 0 and APM to 254... but I get errors.  Here is my /etc/hdparm.conf:
```

# -q be quiet
#quiet 

/dev/sda {
apm = 254
spindown_time = 0
}

/dev/sdb {
apm = 254
spindown_time = 0
}

/dev/sdc {
apm = 254
spindown_time = 0
}

/dev/sdd {
apm = 254
spindown_time = 0
}

/dev/sde {
apm = 254
spindown_time = 0
}

```

Then i restart hdparm:
```

root@monster:~# /etc/init.d/hdparm restart
 * Setting disc parameters...                                                                                                                                                                                                                  
/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
 setting standby to 0 (off)

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
 setting standby to 0 (off)

/dev/sdc:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
 setting standby to 0 (off)

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
 setting standby to 0 (off)

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error
 setting standby to 0 (off)

```

What are the HDIO_DRIVE_CMD input/output errors?

It probably means that the APM value is invalid.

Test with:
```
sudo hdparm -B255 /dev/sd......
```

---

### Post by gnychis on 2008-01-09
> **dcstar said:**
> It probably means that the APM value is invalid.

Test with:
```
sudo hdparm -B255 /dev/sd......
```

Yes, it appears to be giving me an error, why would this be? they're all relatively new SATA drives

---

### Post by enli on 2008-04-02
Bump...

Sometimes my Seagate Sata disk makes lounder noise and UBUNTU completely hangs.So i googled today and many have got problem like this. The solution suggested is to disable the power management for the hard disk. But getting the error as posted below.
I have the same problem i guess.
```
sudo hdparm -B 255 /dev/sda

/dev/sda:
 setting Advanced Power Management level to disabled
 HDIO_DRIVE_CMD failed: Input/output error

```

Any1 got idea?

Edit: Its a DEsktop

---

### Post by chinchillart on 2008-04-05
Same problem with my 500GB Samsung SATA HD.

**After the disk stand-by, when I try to access the disk Ubuntu hangs up and the disk produce a louder noise!!!**

Here the info about the HD

```
 sudo hdparm -i /dev/sda

/dev/sda:

 Model=SAMSUNG HD501LJ                         , FwRev=CR100-11, SerialNo=S0MUJ1NP906859      
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode

```

Keep attention to the note: AdvancedPM = NO

This is the hdparm.conf
```

/dev/sda {
   spindown_time = 120
}

```

When I try to give any command to the disk with HDPARM I get always communication error. Fox Example:
```

 sudo hdparm -X udma5 /dev/sda

/dev/sda:
 setting xfermode to 69 (UltraDMA mode5)
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD(setxfermode) failed: Input/output error

```

How can I change settings in my HD with HDPARM? 
And why the Ubuntu freeze and the disk produce this louder noise, after the disk stand-by?

In Windows everythings works fine: no noise at all.

---

### Post by mishaokami on 2008-06-17
I think i've had similar problems.  Mind you, my problems have been with USB drives.   There are two modes to save power with hdparm.  These are standby and sleep.  (look at the -Y and -y flags)  For me standby has always worked while sleeping puts the drive to sleep *** and i can never wake it up.

Sometimes, i've had better luck with sdparm (in the apt repos).  But, that said, i just got some new usb->sata dongles that refuse to even work with this.

It is unclear why these sort of features aren't supported better by linux.  It could be that the specs aren't open or that nobody cares.  I have done some research and still can't find out 

hope this helps
misha


***  The click you hear is normal.  It is just the drive going to sleep.  When this happens the drive heads move off the disk and lock.

---

