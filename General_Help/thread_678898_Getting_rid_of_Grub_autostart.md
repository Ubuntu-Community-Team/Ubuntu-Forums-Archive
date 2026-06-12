---
title: "Getting rid of Grub autostart"
date: 2008-01-26
forum: General Help
---

### Post by codeking on 2008-01-26
Is there a way to stop grub from counting down from 10?  So many times when I have wanted to boot up windows I wait to long and get Ubuntu.

---

### Post by taurus on 2008-01-26
Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and place a # in front of this line

```
#timeout   10
```
Then, add this new line under it to prompt you for a selection.

```
prompt
```
Also, you might want to put a # in front of the hiddenmenu so you would get GRUB menu.

```
#hiddenmenu
```

---

