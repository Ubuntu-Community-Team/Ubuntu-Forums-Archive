---
title: "Uninstall GRUB from Windows"
date: 2006-12-27
forum: General Help
---

### Post by Octarine on 2006-12-27
Could someone please help me with removing GRUB from my windows drive please?

As of now I get an error 17 in GRUB on Windows and Linux, and neither boot,

I am running from the ubuntu Live CD version 6.06

Is there any way to remove GRUB from the windows partition using the terminal?

My windows is on hda1

---

### Post by xopher on 2006-12-27
One way of doing this is overwriting GRUB on the MBR with windows boot files. This would make ubuntu non-bootable though.

Boot the windows xp cd, go into recovery (console) mode

When at the prompt, run fixmbr

This application will reinstate the windows boot files and 'voilà', you can boot into windoze again.

PS. You could setup GRUB to dual boot too, my guess is you only have the menu.lst setup  wrongly. If this is what you want, try searching the forums, there are lots of threads about this.

---

