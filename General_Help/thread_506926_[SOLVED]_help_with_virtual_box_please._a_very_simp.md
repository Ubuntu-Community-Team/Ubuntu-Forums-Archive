---
title: "[SOLVED] help with virtual box please. a very simple question."
date: 2007-07-22
forum: General Help
---

### Post by rickycodie on 2007-07-22
so i instaled virtual box last night and used this thread

[http://ubuntuforums.org/showthread.php?t=433359&highlight=installivirutalng+ubuntu+studio+programs](http://ubuntuforums.org/showthread.php?t=433359&highlight=installivirutalng+ubuntu+studio+programs)

there is a part when he says to click on ''install guest additions'. that's where i get stuck. i click it and nothing happens. the drop down just closes.

i get no errors, i've checked the logs. i thnk that it's just that i haven't found and downloaded the iso called guest additions. does anyone know where it is? of course i'm using virtual box to emulate windows (ubuntu rocks).

i posted at the virtualbox forums but no help so far.

---

### Post by testube_babies on 2007-07-22
A few seconds after clicking "install guest additions" it should appear as a mounted CD-ROM in explorer.  If it doesn't, I think you can edit the VM setting (after powering it down) and mount it manually as a CD-ROM.

---

### Post by rickycodie on 2007-07-22
i figured it out, here's how if it's not working for you.

on the menubar above whatever os you're running, click on devices and then cd/dvd, then something like add image. once in that screen, remove it if it's already in there, then add, its directory is file system>opt>virtualbox>additions>guest additions.iso.

from there hit select, and then mount the image. now it should run.

---

