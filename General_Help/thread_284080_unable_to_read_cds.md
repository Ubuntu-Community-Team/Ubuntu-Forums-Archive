---
title: "unable to read cds"
date: 2006-10-25
forum: General Help
---

### Post by glenndavy on 2006-10-25
I cant read iso cds in my dvd-+rw drives anymore. no idea why. dmesg|tail  gives me this, which prob means something to someone, but not to me:
```

[17381286.636000] hdb: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[17381286.636000] hdb: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[17381286.636000] ide: failed opcode was: unknown
[17381286.636000] hdb: ide_intr: huh? expected NULL handler on exit
[17381286.684000] hdb: ATAPI reset complete
[17381286.684000] end_request: I/O error, dev hdb, sector 64
[17381286.684000] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16
```
                                                                    
anyone able to suggest to me what might be going on?

thanks
Glenn

---

### Post by po0f on 2006-10-25
glenndavy,

What chipset does your motherboard use?  Post the output of lspci:
```
$ lspci
```

---

### Post by glenndavy on 2006-10-25
```

lspci on machine 1 Freyja - sony vaio laptop:
glenn@freyja:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:05.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:05.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:08.0 Ethernet controller: Intel Corporation 82562EM/EX/GX - PRO/100 VM (LOM) Ethernet Controller Mobile (rev 03)
06:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
glenn@freyja:~$ ls             

```

Theres another machine of ICH5 ilk that has similar prob, but im not in position to do anything with that at moment

thanks for replying
Glenn

---

### Post by po0f on 2006-10-25
glenndavy,

I thought that it might be problems with the chipset, but obviously not.  Can you confirm that the CD works in other drives, or is it just this laptop that's giving you problems?

---

### Post by glenndavy on 2006-10-25
yep works fine in other drives - not just a cd im afraid - any. just not in this one, and the ich5 machine i referred to. the thing is both these drives used to read and write cds with no issue - then mths ago they both stopped - I never chased it then, and now I dont know if it happened exactly same time - i.e. after a dist-get upgrade, or someother event, or...? i've just lived with it till now, but i decided its time to sort it out.
glenn

---

### Post by po0f on 2006-10-25
glenndavy,

Is this just a problem with ISO images, ie do data CDs work fine?  If so, there is a problem with the way you are burning the ISO onto the CD.

---

### Post by glenndavy on 2006-10-25
as an aside i noticed to day i couldnt boot off these drives either - im setting up DSL on a usb keyring so I can see if i can access them independent of ubuntu (or ubuntu in its state on my machines) - but i suspect that wont reveal anything. i learned today that apparently dvd writers have flashable firmware - perhaps thats gone south?

anyhow thanks for your input
glenn

---

### Post by glenndavy on 2006-10-25
>  Is this just a problem with ISO images, ie do data CDs work fine? If so, there is a problem with the way you are burning the ISO onto the CD.

i dont think so - though the ideas a good one - Ive just looked at a (legit) windows server 2003 disk, and an office cd - or tried to...

I get this error:
```

glenn@freyja:~$ mount /media/cdrom
mount: block device /dev/hdb is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``` 
and if I dmesg, i get the output that started the thread.

---

