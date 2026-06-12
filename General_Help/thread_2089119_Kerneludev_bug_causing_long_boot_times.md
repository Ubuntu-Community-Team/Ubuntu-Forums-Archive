---
title: "Kernel/udev bug causing long boot times"
date: 2012-11-28
forum: General Help
---

### Post by El Zoido on 2012-11-28
Hello,

For a while now (at least since 11.10, I think) I was troubled by long boot times in Ubuntu.
A few seconds in, the boot process just hangs for ~30s before continuing normally.

With dmesg I could pinpoint the hang to this lines:

```
ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
ata2.00: failed command: IDENTIFY PACKET DEVICE
```

Finally I found out what's the cause:
A kernel/udev bug that causes some problems with certain SATA CD/DVD drives manufactured by TSSTcorp and Samsung.

See this bug report for Fedora/Redhat [here]("https://bugzilla.redhat.com/show_bug.cgi?id=684599").

Incidentally, I did have troubles with burning DVD/CD in Ubuntu on occasions, which might be related to this bug.

There's a workaround described there, but I'm not sure if that will cause performance degradation on my other SATA devices (HDD).

There's also another solution outlined in the ArchLinux forums [here]("https://bbs.archlinux.org/viewtopic.php?pid=894147").
This one however involves recompiling the kernel, something I never did and frankly have no idea how to do or real interest in finding out.
For now I have "solved" it by exchanging my DVD drive with one from a Windows-only machine (the drive works fine in Windows).

---

