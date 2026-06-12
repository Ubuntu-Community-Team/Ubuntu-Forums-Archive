---
title: "Disable automatic boot from grub"
date: 2008-03-01
forum: General Help
---

### Post by DonDodge on 2008-03-01
I prefer that my grub  wait for me to choose which OS I want booted.

Is there a way to do this or is the best option available to set the timeout to some arbitrarily high number of seconds?

---

### Post by taurus on 2008-03-01
Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and place a # in front of the timeout entry.

```
#timeout   3
```
Then, add the prompt entry in the next line to prompt for your input at the GRUB menu.

```
prompt
```
Save it and reboot.

---

### Post by DonDodge on 2008-03-01
Thank you.

---

