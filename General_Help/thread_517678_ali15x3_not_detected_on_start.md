---
title: "ali15x3 not detected on start"
date: 2007-08-04
forum: General Help
---

### Post by VChief on 2007-08-04
Ok, so having a problem. Installed 7.04 on my wife's computer and the install went fine. Well, the first couple boots didn't want to work. Third one booted then it started up again. I dropped down to watch the messages and saw it was getting stuck on this:

```
ali15x3_smbus 0000:00:11.0: ALI15X3_SMB region uninitialized - upgrade BIOS or use force_addr=0xaddr
ali15x3_smbus 0000:00:11.0: ALI5X3 not detected, module not inserted
```

Did a search and found something vaguely referencing it to UDMA issues. So, I managed to boot single user mode and turned DMA off with hdparm. That didn't work. So, I booted single user mode again and put it back. Now, I notice it won't boot single user anymore. But, it stops at a different line. It stops at.

```
usbcore: registered new interface driver hiddev
```

Back to the DMA thing. I ran diagnostics on the drive and they came back good. Then I noticed something. At the end of my BIOS messages, right before GRUB starts up I get:

```
IDE channel no 80 conductor cable installed.
```

Well, thought that maybe my cable was bad. Got a new cable and it still comes up. I decided to try to install something else. Had a CD of PC-BSD laying around and tried that. Looks like it's definitely a DMA issue. I get multiple 

```
FAILURE: READ_DMA
```

errors (status=51, error=84). So, I'm guessing it's the IDE controller. Any other ideas? Unfortunately, I can't find anything in the BIOS to turn off DMA. I've messed around a lot, but the BIOS always kicks back that the hd's UDMA code is 4.

---

