---
title: "Boot Screens"
date: 2007-11-03
forum: General Help
---

### Post by thetimekeeper on 2007-11-03
I am very confused about the boot screens. The screen with Ubuntu and the progress slider that appears when you boot up and/or shut down.

Is it possible or not to change it, rather than just a static image but with the loading bars? I also came across something for Dapper I think that could show both those items, and a running count of all the boot processes (the part where the messages scroll up with OK etc) below it on the same screen.

It would be great if someone could give me some tips or point me in the right direction :).

EDIT: I use GRUB to dual boot with XP, running Gutsy Gibbon.

---

### Post by mali2297 on 2007-11-03
If you want to see some messages below the progress bar then you can remove the word **quiet** from the following line in the file **/boot/grub/menu.lst**.:

```

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=io7ytrpg3bfpie8ygswqib ro quiet splash

```

:!: Caution. Don't mess up that file.

---

