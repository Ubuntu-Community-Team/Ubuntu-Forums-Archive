---
title: "Gutsy suddenly taking long to boot up"
date: 2008-01-26
forum: General Help
---

### Post by fireman biff on 2008-01-26
Hi, I have a friend's Sony Vaio laptop which is dual booting Gutsy and Vista (both installed by me). Recently Gutsy has started taking much longer to boot up than it used to. The delay occurs after logging in and after the splash screen appears, but before the wallpaper and panel appear.

I'm not sure how to begin figuring this one out. Any pointers?

---

### Post by kuja on 2008-01-26
Try turning off the splash screen and see if you can tell where something is going wrong by seeing where it gets stuck. Also take a look at the /var/log/dmesg and perhaps other log files to see if there are any problems - oftentime they can be blaringly obvious .... if it sounds like an error it very well may be.

---

### Post by fireman biff on 2008-01-28
> **kuja said:**
> Try turning off the splash screen and see if you can tell where something is going wrong by seeing where it gets stuck. Also take a look at the /var/log/dmesg and perhaps other log files to see if there are any problems - oftentime they can be blaringly obvious .... if it sounds like an error it very well may be.

Hi, sorry for taking so long to get back to you.

I actually just turned on the splash screen and disabled the automatic login so that I could get a better idea of where the delay is. So the problem was happening before the splash screen was set to display. As mentioned the delay seems to be after the login and after the splash screen but before the wallpaper and panels appear.

I ran dmesg but I'm really not sure what to do with the results. Here are a couple of the lines that stood out to me:

```
[    5.608000] Attempting manual resume
[    5.608000] swsusp: Resume From Partition 8:5
[    5.608000] PM: Checking swsusp image.
[    5.608000] PM: Resume from disk failed.

```

```
[   18.936000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   18.936000] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
[   18.940000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   18.940000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   18.940000] sonypi: device allocated minor is 63
[   18.940000] input: Sony Vaio Jogdial as /class/input/input6
[   18.944000] input: Sony Vaio Keys as /class/input/input7
[   18.988000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   19.028000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
[   19.072000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
[   19.116000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   19.244000] sony-laptop: Sony Notebook Control Driver v0.5.
[   19.244000] input: Sony Vaio Keys as /class/input/input8
[   19.244000] input: Sony Vaio Jogdial as /class/input/input9
[   19.432000] Failure registering capabilities with primary security module.

```

```
[   22.588000] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

```
[  921.588000] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  921.588000] ata3.00: (BMDMA stat 0x25)
[  921.588000] ata3.00: cmd c8/00:08:a3:d5:b0/00:00:00:00:00/e2 tag 0 cdb 0x0 data 4096 in
[  921.588000]          res 51/40:03:a8:d5:b0/00:00:00:00:00/e2 Emask 0x9 (media error)
[  921.616000] ata3.00: configured for UDMA/100
[  921.616000] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  921.616000] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  921.616000] Descriptor sense data with sense descriptors (in hex):
[  921.616000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  921.616000]         02 b0 d5 a8 
[  921.616000] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  921.616000] end_request: I/O error, dev sda, sector 45143464
[  921.616000] ata3: EH complete
```

I'm not sure what any of that actually means and if it's important/related. By the way, the first 5 lines from the last set of output were repeated several times before the part i copied and pasted.

---

