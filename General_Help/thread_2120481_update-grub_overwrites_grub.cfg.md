---
title: "update-grub overwrites grub.cfg"
date: 2013-02-26
forum: General Help
---

### Post by Parckwart on 2013-02-26
Hi! Everytime I run the update-grub command it overwrites the changes I did to grub.cfg. I'm trying to change the timeout. Any suggestions? Thanks :)

---

### Post by malspa on 2013-02-26
Yeah, see Ubuntu's documentation: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

> grub.cfg is overwritten by certain Grub 2 package updates, whenever a kernel is added or removed, or when the user runs update-grub.

Also see the section, "Timed Display," regarding /etc/default/grub.

---

### Post by schragge on 2013-02-26
Set timeout in the file /etc/default/grub (GRUB_TIMEOUT=), then run 
*sudo update-grub*.

In grub 2.0, grub.cfg shouldn't be edited directly.

---

### Post by Parckwart on 2013-02-26
> **schragge said:**
> Set timeout in the file /etc/default/grub (GRUB_TIMEOUT=), then run 
*sudo update-grub*.

In grub 2.0, grub.cfg shouldn't be edited directly.

Worked. Thank you! :)

---

