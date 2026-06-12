---
title: "boot list"
date: 2008-06-17
forum: General Help
---

### Post by mr.farenheit on 2008-06-17
i ran a fresh install of 7.10 and the only prob so far is that after grub it does not show the preboot list. is there any way to make it show up?

---

### Post by forestpixie on 2008-06-17
Esc - usually. If you want it to not be hidden edit the file

```
gksu gedit /boot/grub/menu.lst
```

change

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

to

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

save and it should be visible on boot - if the time is too quick, change the

> timeout		3
 to suit

---

### Post by VMC on 2008-06-17
> **mr.farenheit said:**
> i ran a fresh install of 7.10 and the only prob so far is that after grub it does not show the preboot list. is there any way to make it show up?

output menu.list:

```
cat /boot/grub/menu.lst
```

---

### Post by mr.farenheit on 2008-06-17
thank you much gang:)

---

