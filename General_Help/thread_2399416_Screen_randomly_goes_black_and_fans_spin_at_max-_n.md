---
title: "Screen randomly goes black and fans spin at max- no overheat"
date: 2018-08-24
forum: General Help
---

### Post by tangent82 on 2018-08-24
Since about Tuesday of this week, my computer has been having a strange error in normal use (watching youtube while working on documents). The screen just goes black out of nowhere, even if I'm only watching a video and not actively doing any input. Audio continues to play, but the computer's fans spin up to max speed, and all I can do is hard reset (no response from keyboard, so far as I can tell). I thought this was overheating, but the BiOS says that temperatures are pretty normal immediately on reboot, so that seems unlikely. The syslog also says nothing about overheating. Instead, what it says it this:

[https://paste.ubuntu.com/p/7gM7HcNRPv/](https://paste.ubuntu.com/p/7gM7HcNRPv/)


This is from the most recent indcident, and while the /00/ thing is new, the rest is the same. Does anyone have any idea why systemd would start flushing the journal without warning like this? Is this related to the most recent kernel update? Should I revert to an earlier kernel? Upgrade to a newer one not in the LTS repos?

Any guidance would be greatly appreciated. I really need to be able to use my computer wtihout constantly being afraid it will randomly fail without warning.

Thank you for your time!

---

### Post by tangent82 on 2018-08-28
Can anyone help? I've tried switiching from the nvidia drivers to open-source drivers, changing my kernel version, none of it changes anything. Now this is happening every 20 minutes or so of uptime. Please, anyone?

---

