---
title: "Restore GRUB default Font"
date: 2012-12-22
forum: General Help
---

### Post by GameX2 on 2012-12-22
Hi,


Quick question: I've tried changing the Font of GRUB using GRUB-Customizer, and now the caracter " - " appear as a " ? " in a bounding box, which look extremely ugly. :mad:

How can I restore the default font?
I went back in GRUB-Customizer, and tried changing the Font to "Monospace", "Ubuntu Mono", "Courrier New", no Font display proprely anymore.

Thanks for the help!

---

### Post by GameX2 on 2012-12-22
Solved;

I just reinstalled GRUB - it was needed, since after I deleted an  HOME partition on a older Ubuntu installed, GRUB deleted itself.  Restoring GRUB with Boot-Repair restored the default settings.

---

### Post by puigpuig on 2013-10-05
I had the same problem and for me the only solution has been, effectively, restoring grub with Boot-Repair.

---

### Post by deadflowr on 2013-10-06
Before trying to reinstall or running programs like boot-repair, which I do normally enthusiastically endorse, 
first look in the file /etc/default/grub.
And see if a line like GRUB_FONT= exists, then open a text editor as root
and add a hash (#) symbol in front to comment out the line.
Then save and run update-grub.

---

