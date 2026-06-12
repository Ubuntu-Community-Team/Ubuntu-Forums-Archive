---
title: "Terrible drive performance under 8.04 / 2.6.24-16-generic"
date: 2008-04-17
forum: General Help
---

### Post by motionsiren on 2008-04-17
I am experiencing some difficulties using a IDE drive under Ubuntu 8.04. I have noticed that PATA disks are now accessed through SCSI Emulation and that *should* be a Good Thing(tm) however....

Im running an OEM Dell Dimension 2350 and here is my hdparm (should I use sdparm?)

```

deb@gratis:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   348 MB in  2.00 seconds = 173.70 MB/sec
 Timing buffered disk reads:  142 MB in  3.01 seconds =  47.15 MB/sec

```

and this is the latest beta, 8.04 - I doub this problem will be squashed before the big release day (9days)

```

deb@gratis:~$ uname -a
Linux gratis 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

```

Everything is running great besides the hdd. Even compiz is nice and smooth (when there is no WAIT on the CPU). 

I found this in my dmesg  (most interesting part)
```

[   16.733776] scsi 0:0:0:0: Direct-Access     ATA      ST3120026A       8.01 PQ: 0 ANSI: 5
[   16.734751] scsi 1:0:0:0: CD-ROM            SAMSUNG  DVD-ROM SD-616T  F310 PQ: 0 ANSI: 5
[   16.735330] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8481B  C102 PQ: 0 ANSI: 5
[   16.752715] Driver 'sd' needs updating - please use bus_type methods
[   16.752843] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   16.752864] sd 0:0:0:0: [sda] Write Protect is off
[   16.752868] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.752898] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.752971] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   16.752988] sd 0:0:0:0: [sda] Write Protect is off
[   16.752991] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.753019] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.753025]  sda:<4>Driver 'sr' needs updating - please use bus_type methods

```
here is my entire dmesg output: [http://dpaste.com/45591/](http://dpaste.com/45591/)

I have read that I should comment out the UUID mounts in my /etc/fstab and instead, define /dev/hda lines but Im hoping for a more forward compatible solution as this is my mothers computer and I will be admining remotely once I set this machine up.

I have also checked BIOS, there is only one feature modifiable that might be related, ACPI... options are either S1 or S3, it was set on S3 (by default? - i Never changed it.)

Any ideas? I have found numerous threads / tickets and pages on the net but NOT A SINGLE ONE has supplied a solution. I'm completely baffled and stumped. This is a major bug for some users.

---

### Post by motionsiren on 2008-04-17
Also, for what it's worth

```

deb@gratis:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:06.0 Communication controller: Conexant Unknown device 2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

```

---

