---
title: "Ubuntu Xenial 16.04LTS Kernel panic - not syncing: VFS: unable to mount root fs on un"
date: 2016-05-18
forum: General Help
---

### Post by mike4ubuntu on 2016-05-18
when trying to boot from 16.04 Live USB, I get this error.

```
Ubuntu Xenial 16.04LTS Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(2,0)
```

I've used this USB thumbdrive on other systems that work fine and have it installed.  Not sure if it is some kind of BIOS setting or the fact that I also have Windows 10 installed on a hard disk.  Any ideas?

---

### Post by QDR06VV9 on 2016-05-18
In order to fix this issue:
1. Boot from Ubuntu install cd
2. Enter Rescue Mode
3. Follow wizzard
4. Execute shell
And enter this in the termnal
5. update-initramfs -u
6. update-grub
7. Remove ubuntu install cd
8. reboot system
Hope this works for you also.
Kind Regards

---

### Post by mike4ubuntu on 2016-05-18
well, the solution which worked for me was just to re-create the USB Live thumbdrive.  Based on some other threads, I guessed that maybe the thumbdrive was corrupted.  I remembered that I had put the thumbdrive into the USB port when I actually was running Microsoft Windows 10 getting ready to reboot the machine, and I think I noticed a Microsoft message that said that the thumbdrive was converted.  Converted to what I don't know, but it looked ok initially when the folder window opened up, so I didn't pay too much attention to it.  Damn Microsoft.  At anyrate, after I re-created it, it booted just fine.  If Ubuntu would have better audio device drivers for the sound recording devices I use, I would have no use for Microsoft.

---

### Post by QDR06VV9 on 2016-05-19
Hey that is good news! Glad you got it figured out...And thanks for sharing your solution.
Cheers

---

