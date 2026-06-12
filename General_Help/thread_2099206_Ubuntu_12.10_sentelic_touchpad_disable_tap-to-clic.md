---
title: "Ubuntu 12.10 sentelic touchpad disable tap-to-click"
date: 2012-12-28
forum: General Help
---

### Post by dash86no on 2012-12-28
Hello. 

I'm on 64 bit 12.10. 

I've been on the same hardware for a few years now. I have a sentelic touchpad, and was initially very annoyed by the tap-to-click "feature" that basically means that my cursor jumps around while I'm typing and I am always inadvertently clicking things. 

I remember disabling it a few years back by adding the following to my rc.local file:

echo -n 0 > /sys/devices/platform/i8042/serio1/vscroll
echo -n c > /sys/devices/platform/i8042/serio1/flags
echo -n 0 > /sys/devices/platform/i8042/serio1/hscroll

However, all of a sudden the dreaded "tap-to-click" is back. I manually ran the rc.local script and confirmed that the /sys/devices/platform/i8042/serio1/flags file does indeed contain a lower case c. However, the curse of tap-to-click is still with me. 

What has happened to stop this fix working, I wonder? 

Any pointers would be most appreciated.

---

### Post by dash86no on 2012-12-29
Apologies, I was too quick to post. 

I fixed the issue with a simple restart. I think what happened was that I'd recently changed my screen turn off setting to turn off after 1 minute of inactivity. I suppose that the screen being locked was possibly affecting my mouse settings. 

I've reset the screen to be locked after 30 minutes of inactivity and I expect that the issue is now resolved, as I never leave my laptop inactive for more than 30 mins.

---

