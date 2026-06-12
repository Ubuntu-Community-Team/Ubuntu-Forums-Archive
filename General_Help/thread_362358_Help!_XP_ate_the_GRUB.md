---
title: "Help! XP ate the GRUB"
date: 2007-02-15
forum: General Help
---

### Post by revcol on 2007-02-15
A Classic tale of two HD's! However this time after XP overwrote Grub during a reinstall, booting from an Ubuntu 6.06 live cd and reinstalling GRUB hasn't worked. Starting with sudo grub from the terminal window thru find, root, setup etc. all worked flawlessly and message said successful install. On reboot however XP sails right thru and launches as though nothing ever happened.

As a second action, I made a GAG boot disk, but again while XP launches fine from the disk, the Ubuntu boot results in a Dos screen with one word - GRUB - and no boot.

I finally have burned a SUPER GRUB boot cd and have been able to access my Ubuntu files, but I'm still puzzled as to why the grub reinstall and then GAG didn't work. Anybody have thoughts on this?

---

### Post by gnu2tux on 2007-02-15
Hi,

Grab an ubuntu CD. Ensure your bios is set to boot from CD first (before hard drive), and then boot from it.

Mount your linux partition and install grub to it, eg:

```

sudo grub-install (hd0)

```

That should get you going again, if not gimme a shout back.

Cheers,

Ali

---

### Post by revcol on 2007-02-17
ALI:  It worked, Many Thanks, revcol

---

