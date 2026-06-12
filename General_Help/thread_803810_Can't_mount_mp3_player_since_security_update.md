---
title: "Can't mount mp3 player since security update"
date: 2008-05-22
forum: General Help
---

### Post by dai_vernon on 2008-05-22
I installed the security update today, and after I did I couldn't unmount my mp3 player/external HD.  Rebooting successfully unmounted it, but now, I can't mount it at all.

Trying to gives this error:

A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal")

How do I fix this problem?

---

### Post by dai_vernon on 2008-05-22
The same mesaage also appears when I try to mount the HFS+ partition that I use when I run OS X.  The CD drive will mount things fine.  Is there some way that I can whitelist these devices to be able to mount?  The error seems to sound like they are rejected for security reasons.

---

### Post by dai_vernon on 2008-05-22
Using sudo mount allowed me to mount it, but I'm still confused as to why I can't mount it automatically.

Also, attempting to unmount it gives the same error message.

---

### Post by jrgns on 2008-07-22
I've got the same problem with my external hard drive. Anyone got any fixes for this? I can mount it manually, but I want it to happen automatically.

Can't seem to find any concrete answers on the web as well...

---

