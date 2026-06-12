---
title: "plymouth only text"
date: 2014-07-31
forum: General Help
---

### Post by danjde on 2014-07-31
hi friends,
I've started and installed ubuntu 14.04 using the option "xforcevesa" (graphical plymouth was start, but there was some problem for gdm3)

Now, to the installed system, all works fine except for the plymouth splash screen that stay only on text mode;


I've set the plymouth alternaive:

```
update-alternatives --config default.plymouth
  Selezione    Percorso                                                           Priorità  Stato
------------------------------------------------------------
  0            /lib/plymouth/themes/ubuntu-gnome-logo/ubuntu-gnome-logo.plymouth   150       modalità automatica
* 1            /lib/plymouth/themes/ubuntu-gnome-logo/ubuntu-gnome-logo.plymouth   150       modalità manuale
  2            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo-scale-2.plymouth       99        modalità manuale
  3            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth               100       modalità manuale


```

and then rebuild initrd:

```
update-initramfs -u
```

I've verifyed /etc/default/grub:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```


but nothing, plymouth stay only text

could you suggest where I should make the changes?

---

