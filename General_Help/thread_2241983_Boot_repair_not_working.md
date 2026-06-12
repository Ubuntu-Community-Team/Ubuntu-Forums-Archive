---
title: "Boot repair not working"
date: 2014-08-29
forum: General Help
---

### Post by tyler49 on 2014-08-29
Somehow my bootloader / boot partition got messed up.

Legacy boot is disabled in bios, only EFI boot is allowed.

Boot repair continuously tells me about GPT detected. Please create boot partition.

Although I have a fat32 partition at the start of the drive with the boot flag set.

Here's the pastebin: [http://paste.ubuntu.com/8182000/](http://paste.ubuntu.com/8182000/)

Any help on what to do to get it working?

I tried chrooting to the installed OS from the live disk and doing a grub install from there, but that failed as well.

---

### Post by tyler49 on 2014-08-29
ok, I got efi bootloader reinstalled by using apt --reinstall.

however, when it boots now, all I get is a blank screen... Even with the quiet and splash options removed from grub.

---

