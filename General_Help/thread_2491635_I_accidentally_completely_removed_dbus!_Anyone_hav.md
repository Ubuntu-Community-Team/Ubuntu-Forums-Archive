---
title: "I accidentally completely removed dbus! Anyone have an idea to fix this?"
date: 2023-10-16
forum: General Help
---

### Post by samuriCat on 2023-10-16
I cannot believe I did this, but in thinking I was removing "ibus" I accidentally completely removed dbus (Ubuntu Studio 22.04). Any ideas how to fix this? I can't connect to the internet with the laptop, but I might be able to burn an installation disk.

Apologies in advance.

---

### Post by HermanAB on 2023-10-16
Dbus is so fundamental, you probably need to backup your data and reinstall the whole kit and kaboodle.  However you could try only reinstalling Gnome or whichever DE you use and see if things work again.

---

### Post by samuriCat on 2023-10-16
Thanks, I guess it's time reinstall. Ugh!

---

### Post by ActionParsnip on 2023-10-16
would a chroot work?

---

### Post by samuriCat on 2023-10-16
Sorry, already reinstalled Ubuntustudio!

---

### Post by MAFoElffen on 2023-10-16
> **ActionParsnip said:**
> would a chroot work?
Too late seeing this (he already did a re-install) 

For other users seeing this later... That is what I would have done.

chroot into the installed system, and reinstalled 'ubuntu-studio', which was his desktop package. That would have reinstalled dbus.

[HR][/HR]
This is why I had started the Ama-Gi Project (based on ubuntu-standard), was to create a bootable, portable, basic Linux Live Image Environment, from which to chroot into an installed Linux system to repair it... Sort of like the Boot Repair disk does for the boot loader (Grub2). Life got in the way of it's progress, but the need is still there.

---

