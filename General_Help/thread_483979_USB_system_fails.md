---
title: "USB system fails"
date: 2007-06-25
forum: General Help
---

### Post by mikesmith00 on 2007-06-25
I've been running Ubuntu Feisty for about 2 months now, and really like the OS, but I have one major problem that seems to have come up recently.  Randomly (I've tried to narrow down what triggers it, but the only program that has been running every time is pidgin) I lose my wireless connection, completely.  The only way to bring it back up is by doing a hardware reboot.  I started running some tests, and the resolv.conf file stays the same, the only change that I can tell is that I completely lose USB function (This is a USB wireless dongle under ndiswrapper).  I run lsusb from terminal, and the cursor blinks, but it never returns control at prompt to me, I have to shutdown terminal and restart.  At times, it will be up for 2 or 3 hours at a time, othertimes it'll be up for only 3 or 4 minutes at a time.  It seems as though there is still power coming from the USB ports, because the lights on the dongle still blink, it just doesn't seem as though ubuntu will acknowledge that they're connected.  If you have any advice on how to fix this, that would be greatly appreciated.


EDIT:  Problem solved, it was a hardware failure.

---

