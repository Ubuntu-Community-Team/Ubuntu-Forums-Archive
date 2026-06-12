---
title: "Grub menu.lst location change"
date: 2007-09-30
forum: General Help
---

### Post by snappy46 on 2007-09-30
Good day,

Sorry for asking probably a simple question that might have been answered a thousand time but here is my problem.  When my computer boots up and grub gets loaded it always seem to point to the wrong partition /boot/grub/menu.lst on /dev/hda4 where I still have Mepis installed but I am not using anymore since I switch to Ubuntu about a year ago.  The problem is that when an upgrade requiring modification of the menu.lst file is required ubuntu of course update the /boot/grub/menu.lst file that is present on the partition that it is loaded on which is /dev/hda2 and I have to manually copy the new data from the file in hda4 to hda2 to be able to boot properly.

Ok here comes the stupid (simple) question:  How do I get the MBR/grub to point to the menu.lst on /dev/hda2 vice /dev/hda4 as it does presently.

Thank you

---

### Post by logos34 on 2007-09-30
**sudo grub-install /dev/hda**
[B]
sudo update-grub[/B]

check that the 'groot' and 'root' lines in menu.lst point to **(hd0,1)**

---

### Post by snappy46 on 2007-09-30
Thank you for the quick response.  Worked perfectly.

---

