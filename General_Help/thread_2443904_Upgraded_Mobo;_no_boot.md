---
title: "Upgraded Mobo; no boot"
date: 2020-05-21
forum: General Help
---

### Post by jhite-h on 2020-05-21
I got a new motherboard, cpu, and ram and installed my current drives. System was working. Bios detects all the drives correctly. But it says none of them are bootable. It was a dual boot system. Never booted into windows really but in case it matters. But it's not trying to boot and not finding grub. It's saying none of the drives are boot drives. 
So how do I fix that? Obviously liveboot, but then what? Boot repair won't fix this will it?

---

### Post by TheFu on 2020-05-21
Use boot-repair to run a report and post the URL.  Do not run the "fix" process it offers. That could make things worse.

---

### Post by lvm on 2020-05-22
It may be EFI-related. Make sure secure boot is off in BIOS (UEFI) settings, upgrade BIOS to the latest version. If 'ubuntu' appears in BIOS boot targets, select it as primary.

---

### Post by jhite-h on 2020-05-22
Thanks, it was an EFI problem. As in, new motherboard doesn't support legacy and the old install is a direct upgrade from pre 2012 to 18.04. So I had to make an EFI partition and then do boot repair. It has been so long since I tried to do anything like this I was completely stumped for a minute.

---

