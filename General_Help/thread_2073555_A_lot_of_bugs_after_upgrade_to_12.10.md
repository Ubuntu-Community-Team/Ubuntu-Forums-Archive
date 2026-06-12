---
title: "A lot of bugs after upgrade to 12.10"
date: 2012-10-19
forum: General Help
---

### Post by azcv on 2012-10-19
I have upgraded to 12.10 the usual way and after upgrade i have the folowing issues:
1.I can't edit software sources from the application.The only way is with gedit manualy.
2.When the sreen dims the bottom edge of the panel starts blinking.
3.The bug with network indicator is not fixed in 12.10(missing menu entries)
4.The system boots slower than 12.04
5.The dash is slower than ever,but i am not using this.I prefer classic menu indicator.
6.When i open  folder as root either in nautilus or pcmanfm the ubuntu scrolbars transforms into traditional scrolbars and the menus go below the panel.That happens also with all applications opened as root(gedit).

---

### Post by ricardisimo on 2012-10-19
"Lock" (I'm assuming this is supposed to be "lock screen" or "lock account" does nothing now.

---

### Post by pandacookie on 2012-10-19
> **ricardisimo said:**
> "Lock" (I'm assuming this is supposed to be "lock screen" or "lock account" does nothing now.

That's odd. It works for me.

---

### Post by MrsUser on 2012-10-20
I had those issues with 12.04 unless I did a fresh re-install. Upgrades never work for me. For some reason upgrades always slow down my system or mess things up. I recommend to do a fresh install. Here's a nice and quick tutorial to do a fresh install within very little time, with backin up your software configs etc:

[http://www.matthartley.com/how-to-backup-your-ubuntu-software/](http://www.matthartley.com/how-to-backup-your-ubuntu-software/)

---

### Post by azcv on 2012-10-22
Thank you for your advice.I will wait for the first official updates after the final release.If the problems persist i will think about of a fresh install.I have not time for this right now.
If someone have a solution for one or more of this issues please post it. Thank you.

---

### Post by kiaeix on 2012-10-22
I can not safely remove (detach) an external hard drive through Nautilus. The only workaround is

```
sudo udisks --detach
```

what is unnice.

[LIST]
[*]unmounting is no problem at all
[*]detaching USB flash drive is no problem
[*]detaching USB hard drive is a problem
[/LIST]
Does anybody have similar experiences? Or perhaps a solution?

---

