---
title: "Recovery menu is a mess on-screen"
date: 2021-02-20
forum: General Help
---

### Post by Paddy Landau on 2021-02-20
Ever since I installed Ubuntu 20.04, the Recovery Mode menu has had a bunch of messages overwriting it. I've attached a screenshot.

The menu still works, but of course reading the individual items is hard and sometimes impossible.

It's not a big problem (I hardly ever use it), but I'd like to fix it.

More information:

[LIST]
[*]Ubuntu 20.04
[*]Installed with the default installer using UEFI and full-disk encryption with LUKS and LVM (erasing everything that was on the disk previously)
[/LIST]
Thank you

---

### Post by vanadium on 2021-02-21
We had a discussion on this in the [Dutch forum]("https://forum.ubuntu-nl.org/index.php?topic=108275.25"). Looks like some configuration bug. The easiest way around would be to just press "Esc" on the garbled menu:  that redraws the menu and then you can properly see.

A workaround would be to eliminate bootmessages by adding "quiet": 'GRUB_CMDLINE_LINUX="quiet"'. That suppresses the boot messages. However, when you go into recovery, you likely want to see these messages.

---

### Post by Paddy Landau on 2021-02-21
> **vanadium said:**
> … press "Esc" on the garbled menu
I didn't know that! Yes, Esc works for me.

I won't bother worrying about the configuration; it's too much hassle. I'll press Esc as you suggest.

Thank you!

---

