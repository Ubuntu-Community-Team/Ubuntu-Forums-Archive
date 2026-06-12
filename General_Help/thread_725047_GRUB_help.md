---
title: "GRUB help"
date: 2008-03-15
forum: General Help
---

### Post by zjgz on 2008-03-15
I'm going to try to start using ubuntu again, but one of the problems i've had with it is that i don't like that GRUB is set up to default boot to ubuntu. What I want to do is set it up so it would automatically go to windows. Any way i can do this?

---

### Post by dabang on 2008-03-15
This is pretty easy:

```
sudo gedit /boot/grub/menu.lst
```

search for:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default    0
```

Change "default 0" accordingly. For example, if windows is the fourth entry in your grub menu, change to "3". (Starts counting at zero)

---

