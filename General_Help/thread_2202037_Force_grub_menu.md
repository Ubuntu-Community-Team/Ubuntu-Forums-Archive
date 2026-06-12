---
title: "Force grub menu"
date: 2014-01-27
forum: General Help
---

### Post by robert48 on 2014-01-27
Hello, I can't get my grub2 menu to show at boot, even when I hold the shift key or escape key down. I suspect this may be because a scsi scanner boots up before the os.

Can someone point me towards the definitive information that details all the commands in the grub.cfg file please?

Many thanks

---

### Post by jeanjd63 on 2014-01-27
Hello
You can edit file grub :
**sudo  gedit  /etc/default/grub**
you comments (with a # in first position) the line :
#GRUB_HIDDEN_TIMEOUT=0
You save and quit gedit and valid the change by :
[B]sudo  update-grub
[/B]At he next boot grub-menu will appears
Bye

---

### Post by robert48 on 2014-03-16
That works! Thank you very much.

---

