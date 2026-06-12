---
title: "suspend broke the system"
date: 2014-07-11
forum: General Help
---

### Post by ship22 on 2014-07-11
So I accidentally hit "suspend" instead of "shutdown" on my HP probook 6470b running ubuntu 14.04 LTS. Now it boots up, retaining iptables setttings I don't want to set (and flushing doesn't seem to fix)... and I cant' shut down. I just get the "Ubuntu" splash and it never shuts down.  I can force power off with the power button, but when I boot, it boots with the same suspended crap and I can't shut down.

Anyone know how to un-hose this?

Not seeing any helpful messages in syslog.  Doesn't seem to be a console anymore. The keyboard is frozen on the term screens, so can't run dmesg.

tried halt, shutdown -h now... won't bloody shut down.

Is there a way to manually clear whatever flag that is making the system suspend/unsuspend?  Based on another thread, it sounds like apparmor is the culprite but I have no idea how to get around it... cant' seem to turn it off.

---

### Post by ship22 on 2014-07-11
shutdown -r works.. but the system still "unsuspends" into a broken state. I can't halt, and I can't escape the suspend status.

---

### Post by stalkingwolf on 2014-07-11
maybe try running the recovery mode and fix broken packages ?

---

### Post by ship22 on 2014-07-11
> **stalkingwolf said:**
> maybe try running the recovery mode and fix broken packages ?

Thank you for suggesting this. I didn't try it but it gave me the idea to try doing a "update-grub", which fixed whatever weirdness was happening.  It then shutdown ok and started up normally.

---

### Post by stalkingwolf on 2014-07-15
recovery is always my first stop .  I find K.I.S.S. is always the easiest and best.

---

