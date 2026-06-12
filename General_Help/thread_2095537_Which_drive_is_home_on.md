---
title: "Which drive is /home on?"
date: 2012-12-17
forum: General Help
---

### Post by Slugbreath on 2012-12-17
Hello! This is most likely a very trivial question, but I have not been able to find an answer to it online. I need to figure out on which hard drive my /home and /boot catalogs are. Is there an easy way to do this?

/Slugbreath

---

### Post by Quarkrad on 2012-12-17
A graphical method of seeing where it is - is to install **gparted** from the Software Centre.  You will see what disk (if you have more than one) and what partition it is on.

---

### Post by Wim Sturkenboom on 2012-12-17
The command _mount_ will show what is mounted; if /home is a separate partition, it will show with the above command.

You can also check the content of the file /etc/fstab.

If /home does not show with above methods, it's on the drive that is mounted as '/'.

---

### Post by Slugbreath on 2012-12-17
Thank you both of you. That worked perfectly.

This can now be marked as solved!

/Slugbreath

---

### Post by Wim Sturkenboom on 2012-12-17
> **Slugbreath said:**
> Thank you both of you. That worked perfectly.Pleasure

> **Slugbreath said:**
> This can now be marked as solved!You can do so yourself using the thread tools just above the first post on this page ;)

---

