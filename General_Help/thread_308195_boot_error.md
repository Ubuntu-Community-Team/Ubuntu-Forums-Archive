---
title: "boot error"
date: 2006-11-27
forum: General Help
---

### Post by dbbolton on 2006-11-27
when i boot the ubuntu kernel, i get this message:
> Setting sensors limits..........................Failed

everything else is ok. the system seems to run fine contrary to that.

any advice?

---

also, i run regular gnome ubuntu, and just installed the packages "xubuntu-desktop" and "kubuntu-desktop" to have the respective choices on my session list. however, now the boot screen (e.g., where i'm getting the error) says "xubuntu" rather than "ubuntu". it's quite annoying. is it possible to revert this, or do i need to get rid of xubuntu?

---

### Post by mssever on 2006-11-27
> **dbbolton said:**
> when i boot the ubuntu kernel, i get this message:


everything else is ok. the system seems to run fine contrary to that.

any advice? I have that error, too. I think it's because our hardware doesn't support the fine-grained control that whatever program that's printing that message (lm-sensors, I think) is trying to set. For example, all I can do on my machine is see the processor temp. There's no harm in that error.
> also, i run regular gnome ubuntu, and just installed the packages "xubuntu-desktop" and "kubuntu-desktop" to have the respective choices on my session list. however, now the boot screen (e.g., where i'm getting the error) says "xubuntu" rather than "ubuntu". it's quite annoying. is it possible to revert this, or do i need to get rid of xubuntu?You just need ro reinstall or reconfigure the appropriate ubuntu package. I think that it's called ubuntu-artwork. You can try re-installing ubuntu-desktop as well, but I don't know if that will solve it. I had that same problem a while back. Unfortunately, I don't remember what package solved it.

EDIT: usplash might also be the package in question...

---

