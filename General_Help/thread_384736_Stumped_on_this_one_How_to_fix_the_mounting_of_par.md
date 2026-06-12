---
title: "Stumped on this one: How to fix the mounting of partitions in edgy"
date: 2007-03-14
forum: General Help
---

### Post by mwinslettTX on 2007-03-14
Howdy all--

I discovered yesterday that Ubuntu (Edgy by the way) won't mount my two separate partitions.  They are both using the NTFS file system.  If i mount them using the command line (to the /media folder), they mount and I can access them through nautilus.  However, they don't show up on the desktop or on the side pane on in the file explorer.  How do I fix this and how do I make this automatic?


Any help on this one would be greatly appreciated!!!

Cheers,
Turbo
:confused: :confused: :confused: :confused:

---

### Post by michael117 on 2007-03-14
If you want them to mount automatically during boot, you would need to edit the /etc/fstab and add the correct lines for your partitions. I believe there is a tool under the system menu somewhere that can automatically add lines to your fstab to accomodate for new partitions to be mounted. I would also suggest doing a search on the ubuntuforums for a how to on ntfs-3g. I believe it has become a lot easier to mount with ntfs-3g now, but check to be sure. Ntfs-3g, by the way, will allow you read AND write support for your ntfs partitions. I think that once you have them correctly in your fstab and they mount correctly on boot, I would imagine ubuntu would add them to the desktop and on the side. If that does not prove to be the case, I would think that somehow you had your settings changed and you would need to correct it somewhere in the gconf editor.

---

### Post by llamakc on 2007-03-14
If memory serves me, the gconf key is at apps|nautilus|desktop & check volumes_visible. You can google or search here to double-check that.

---

