---
title: "Trying to find partition manager after installed Kubuntu"
date: 2018-11-20
forum: General Help
---

### Post by seanspotatobusiness on 2018-11-20
I just installed Kubuntu 18 and I'm now looking for the partition manager but cannot find one installed. Is a partition manager not part of the default installation? It seems like an important thing to include.

---

### Post by HermanAB on 2018-11-20
It is called gparted.

However, if you are not happy with the way the system is partitioned, it is easier to re-install and set the partitions properly that way, than try to fix a mess after.

---

### Post by oldfred on 2018-11-20
You cannot change mounted partitions, so gparted is not included in default install. 
I do install it, but just to partition my other drive, or flash drives.

Gparted is on live installer and most times you have to use live installer to change partitions.

---

### Post by seanspotatobusiness on 2018-11-21
When I open the program menu and type in "gparted", there's nothing there. I have some blank space at the end of my disk and I want to put a partition there so it can be used. I'm not trying to change the partition where the installation is.

---

### Post by QIII on 2018-11-21
No gparted in a live session?

If not, you can install it just as you would on an installed system, but it will not persist in the next session.

---

### Post by HermanAB on 2018-11-21
```
$ sudo apt install gparted
```

However, as said above, you cannot change a partition that is in use, so you should boot with the install disc or USB widget, then run gparted (it is included in there).

---

### Post by monkeybrain20122 on 2018-11-21
I think kubuntu comes with a partition manager called kparted or something..

---

### Post by SeijiSensei on 2018-11-21
KDE has its own partition manager.  If you go to the System part of the main menu, is it not there?

---

