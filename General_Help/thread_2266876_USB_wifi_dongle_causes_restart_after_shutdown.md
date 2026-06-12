---
title: "USB wifi dongle causes restart after shutdown"
date: 2015-02-25
forum: General Help
---

### Post by mlamberg on 2015-02-25
I'm running 12.04 LTS on a Lenova ThinkCentre 8215-zk5.  I recently installed a USB wifi dongle (Rosewell RNWD-N1501UB) which is working great!
When I shutdown the system everything goes well, the shutdown sequence is fully successful, everything including the disk and fans go quiet...  Less than 2 seconds later the system turns back on and reboots.  The system is actually a dual boot machine (ubuntu and Windows XP) running grub as the bootloader.  If I bring up the system on windows I have no problems shutting down.  Only for Ubuntu.  Also if I remove the USB wifi dongle Ubuntu does shutdown properly..  I never changed anything on the bios but checked it anyway, there didn't appear to be any strange power on settings or anything unfamiliar...  If anyone out there can help would really appreciate it..  This USB thing has got me stumped.....

---

### Post by carl4926 on 2015-02-25
You seem to have checked the obvious. It is indeed odd.
If it were a BIOS setting, I thing the phenomena would affect windows too, since it sounds like your BIOS is traditional and OS independent. I say that because I have come across some low end machines with UEFI BIOS that is only accessible thru Windows8.
FYI: XP is no longer considered safe at all

Try some command line shutdown methods:

```
[FONT=Ubuntu Mono]sudo shutdown -h now[/FONT]
```or
```
[FONT=Ubuntu Mono]sudo halt[/FONT]
```or
```
[FONT=Ubuntu Mono]sudo init 0 [/FONT]
```

---

### Post by mlamberg on 2015-02-26
Thanks for replying , I will try those commands when I get home later this evening

---

