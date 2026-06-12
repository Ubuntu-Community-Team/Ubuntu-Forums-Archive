---
title: "GRUB vista booting error 13"
date: 2008-05-02
forum: General Help
---

### Post by goohman on 2008-05-02
I had windows vista/longhorn (loader) in my grub menu. I went from hacked vista to official and restored vista to its normal booting thing.


but now when i pick vista it says resetting boot drive then i get a flash of what looks like code but then vista loaded. so i was like, ok cool it work'd. but now my system freezes when your using it. no cursor movement, caps/shift/numlock control. So i thought it has something to do with grub resetting my HD and it was locking my hd so i edited grub to load just "vista/longhorn" *I only deleted the " (loader)" <see the space>* but now i get error 13 invalad executable or some crap like that....

i need help on booting vista again like i did when i had vista loader just went right through. Ill post my menu.lst file if you want me to.

please help me get back into vista

---

### Post by goohman on 2008-05-02
bump -fell off first page-

---

### Post by goohman on 2008-05-03
bump

---

### Post by Zorael on 2008-05-03
You could let grub try to automatically update that menu.lst.
```
$ sudo update-grub
```

---

### Post by goohman on 2008-05-03
> **Zorael said:**
> You could let grub try to automatically update that menu.lst.
```
$ sudo update-grub
```I did that but it only made more ubuntu entry's windows was untouched, and still errored out

---

### Post by strabes on 2008-05-03
Never edit /boot/grub/menu.lst unless you know **exactly** what you are doing. Anyway, reinstalling grub should fix this problem for you. See the link in my signature.

---

