---
title: "GRUB reinstall"
date: 2007-01-06
forum: General Help
---

### Post by specs10 on 2007-01-06
Okay, so I've been researching this issue for a couple of days now and I'm starting to think that I don't really have any options, but here's my situation:

I just got a logitech MX5000 bluetooth wireless desktop for my dual boot desktop PC.  So far it works perfectly in Ubuntu and in Windows; however, GRUB won't.  I've seen other people solve this problem by enabling legacy USB support in the BIOS, but my BIOS only has two options: USB control by the BIOS or by the OS.  This would solve the problem, I think, but when I turn on BIOS USB control, GRUB (which is installed on an IDE disk) gives me an Error 21.

I had an old GRUB install on the MBR of a SATA drive and when I boot to that disk with BIOS USB control turned on, the keyboard is recognized, but since it's an old install and the paths and stuff are broken, it can't boot anything.

So anyway, I think the solution is to install grub onto one of my SATA disks, but I can't find a HOWTO that works for me.  Most of the HOWTOs seem to be geared towards fixing a broken GRUB install, but I just need to move mine to the MBR of another disk.  If anyone can point me to a good HOWTO or give me some other kind of solution, I'd love them forever.

---

### Post by specs10 on 2007-01-08
bump?  bump.

---

### Post by Buck2348 on 2007-01-08
I'm mostly ignorant about these things, and you've probably seen this thread, but for what it's worth it looks to me as if this tells how to install grub to a partition of your choice: [ http://www.ubuntuforums.org/showthread.php?t=224351]("http://www.ubuntuforums.org/showthread.php?t=224351")

Regards,
Buck

---

### Post by specs10 on 2007-01-09
yeah, I've tried this method a couple times.  and I've also tried it using a different disk than the "find" command produces.  it's entirely possible that I'm doing something wrong, but it just doesn't seem to be working for me.  thanks, though, buck.

I've pretty much resigned myself to the fact that I'll just have to have a ps2 keyboard plugged in to boot with.

---

