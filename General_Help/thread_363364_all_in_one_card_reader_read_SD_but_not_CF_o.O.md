---
title: "all in one card reader read SD but not CF o.O"
date: 2007-02-16
forum: General Help
---

### Post by MeduZa on 2007-02-16
Hello, I have a USB card reader all in one, It work perfect "out of the box", I used only SD/MMC cards and everything is fine, yesterday I try two CF cards (16mb and 128 mb, working on my PDA) and nothing happened, no auto mount, no device on /dev/... 
the card reader create 4 SCSII virtual units at boot on /dev: SDC (SDC1, SDC2 , etc) for SD/MMC, SDD (SDD1, SDD2 , etc ) for the CF and this way for the other two (SDE and SDF)

When I insert my SD card the command dmesg shows this:
sudo dmesg
[ 4886.494000] SCSI device sdc: 494080 512-byte hdwr sectors (253 MB)
[ 4886.504000] sdc: Write Protect is off
[ 4886.504000] sdc: Mode Sense: 03 00 00 00
[ 4886.504000] sdc: assuming drive cache: write through

when I insert a CF card the dmesg shows this and start a loop:
sudo dmesg
[ 4949.076000] SCSI device sdd: 32000 512-byte hdwr sectors (16 MB)
[ 4949.081000] sdd: test WP failed, assume Write Enabled
[ 4949.081000] sdd: assuming drive cache: write through
[ 4949.088000] sdd: Spinning up disk.......................................................................................not responding...
[ 5049.840000] sdd : READ CAPACITY failed.
[ 5049.840000] sdd : status=1, message=00, host=0, driver=08 
[ 5049.840000] sd: Current: sense key: Not Ready
[ 5049.840000]     <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 5049.842000] sdd: test WP failed, assume Write Enabled
[ 5049.842000] sdd: assuming drive cache: write through
[ 5049.854000] sdd: Spinning up disk..............

and loop the spinning up disk!

lsusb shows this:

sudo lsusb
Bus 001 Device 004: ID 046d:c218 Logitech, Inc. 
Bus 001 Device 003: ID 046d:c21a Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0764:0501 Cyber Power System, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04a9:1712 Canon, Inc. 
**Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. **

yes the last one is the card reader

Somebody have a problem like this and solve it?

thank you :wink:

---

### Post by fragos on 2007-02-17
I have a different Alcor reader, ID 058f:9360 Alcor Micro Corp.  I have no such problems.  Spinning up is a term that referes to disk drives.  Perhaps the driver believes your CF card is a CF hard drive.

---

