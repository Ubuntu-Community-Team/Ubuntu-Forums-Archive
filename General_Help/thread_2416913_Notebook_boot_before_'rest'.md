---
title: "Notebook boot before 'rest'"
date: 2019-04-17
forum: General Help
---

### Post by fabim123 on 2019-04-17
I'm with an interesting problem:

I a Dell notebook with ubuntu and windows in dual boot. But, in some cases, it simply don't find any grub, not even windows boot manager works.

The notebook asks for 'retry reboot'. In legacy mode, 'grub rescue'.

Can be a problem in he hard disk, but if I start a live cd, the HD is always recognized and mounted and works fine.

This normally occury after a abrupt restart, example when the battery runs out or a abrupt shutdown in the button. But, sometimes this occur without apparent reason.

The most weird is that the solution is 'rest' the notebook for some hours. It starts normally again!

I tried boot-repair many times, didn't works in this case. But i don't know what can be that 'go and return' only by the time.

Greateful for help!

---

### Post by TheFu on 2019-04-17
HDDs have different parts, called sectors.  The boot sector is used all the time and if it is failing, then boot problems happen.  It could just be that sector that is corrupt, so reinstalling grub would refresh the bits there.  If the disk is GPT, not MBR, then the boot data is put at the beginning AND the end of the disk. 2 copies, far apart, unlike MBR which has 2 copies, right next to each other.

Boot-repair doesn't fix as many issues as it once did.  Run it again, gather the information and post the URL back here for better help.  URL is preferred.

---

### Post by fabim123 on 2019-04-24
I executed the bootinfo of boot-repair:

[http://paste.ubuntu.com/p/NpXVwp3t6W/](http://paste.ubuntu.com/p/NpXVwp3t6W/)

Results of the lest execution of boot-repair:

[https://paste.ubuntu.com/p/QbRKvZHdB9/](https://paste.ubuntu.com/p/QbRKvZHdB9/)

Boot-repair.log

[https://paste.ubuntu.com/p/ZPFt5qHvKs/](https://paste.ubuntu.com/p/ZPFt5qHvKs/)

---

### Post by TheFu on 2019-04-24
Did you see this?

```
BOOT_IMAGE=/boot/vmlinuz-4.18.0-17-generic root=UUID=95e284eb-96d0-43b7-9afb-b988f89b2a93 ro quiet splash vt.handoff=1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)
Windows is hibernated, refused to mount.
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)

```
Looks like you have to get Windows booting first. There isn't any Linux solution to that. Only Windows can handle it. They need to be properly closed, which means disabling fastboot and hibernation (or whatever Windows is calling it these days). [https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/](https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/)

At the bottom of the report is other advice, which I cannot understand. Sorry.

---

