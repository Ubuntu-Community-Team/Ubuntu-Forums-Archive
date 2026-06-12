---
title: "ubuntu restart and load windows automatically"
date: 2019-10-09
forum: General Help
---

### Post by iceze on 2019-10-09
[COLOR=#242729][FONT=Arial]I have an ACPI problem which means I need to boot into Ubuntu and reboot into Windows. The BIOS can't turn ACPI off or otherwise be configured to solve it.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Is there a way to make Ubuntu automatically load as first boot and restart itself and go to windows?

So somehow make Ubuntu load first > automatically restart as soon as the kernel is loaded > make Windows load as a one-off first, it would solve my problem.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How could I find that?[/FONT][/COLOR]

---

### Post by TheFu on 2019-10-10
I don't think that is possible, without re-writing the GRUB menu each time, doing an update-grub, and changing the default OS to boot.  Then you'd have Windows as the default, which is worse than death, IMHO.  ;)

---

### Post by CatKiller on 2019-10-10
> **iceze said:**
> Is there a way to make Ubuntu automatically load as first boot and restart itself and go to windows?
If you're using UEFI, you can use systemd to boot into a different EFI image. I've used it to boot into the system setup, but I understand that it can also load the Windows boot loader (I haven't used Windows for 15 years, so I have no experience of that). I believe the command is systemd-boot, but I'm not near my computer to check

---

