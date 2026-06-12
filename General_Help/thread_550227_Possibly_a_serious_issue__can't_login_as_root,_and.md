---
title: "Possibly a serious issue:  can't login as root, and removed from sudoer file"
date: 2007-09-13
forum: General Help
---

### Post by sgfaulkner on 2007-09-13
I was changing some permissions so my virtual box install can access usb.  Well the group add program did something funky and removed me from a bunch of groups.  Now I am also no longer in the sudoers file.  Also I guess by default you cannot login as root in ubunutu.  So where does that leave me?  Am I permanently screwed out of admin access to my system?

---

### Post by tszanon on 2007-09-13
> **sgfaulkner said:**
> I was changing some permissions so my virtual box install can access usb.  Well the group add program did something funky and removed me from a bunch of groups.  Now I am also no longer in the sudoers file.  Also I guess by default you cannot login as root in ubunutu.  So where does that leave me?  Am I permanently screwed out of admin access to my system?
You can use the live cd to modify the necessary files (I don't know what files). There, you can easily use sudo to gain administrative access to your files.

---

### Post by nick_h on 2007-09-13
When you boot, select the recovery mode option from the grub menu.  This will put you in single user mode as root.  You can then fix your problems.

---

