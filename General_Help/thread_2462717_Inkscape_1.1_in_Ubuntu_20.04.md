---
title: "Inkscape 1.1 in Ubuntu 20.04"
date: 2021-05-26
forum: General Help
---

### Post by grey1beard on 2021-05-26
I've been using Inkscape for several years, and have just seen it updated to 1.1, with improvements.
However, this morning, if I hit the 'Save As' menu, the whole program closes !
In the middle of a rush job (of course) and am somewhat b*****ed.
I've tried re booting, and I will now try upgrade/update in terminal, but grateful for any ideas, or sympathy from anyone else with this problem.
John

---

### Post by Impavidus on 2021-05-26
So I assume you don't use it from the official Ubuntu repos, right? Because those stay at the same version for the entire live of the Ubuntu release (0.92 for Ubuntu 20.04).

---

### Post by grey1beard on 2021-05-26
That's interesting. I didn't know that.
As far as I know, it got updated automatically, I've no idea how.
Anyway, it appears to be a known bug, and I am currently reinstalling it, to see if that works, prior to reverting to an earlier version, as suggested by the Inkscape forum.

EDIT Solved - reinstalling to a new build works.

---

### Post by ajgreeny on 2021-05-26
There is a ppa for inkscape ([https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable?field.series_filter=focal](https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable?field.series_filter=focal)) which supplies 1.1.1.

Is that where you install came from or did you build inkscape yourself from source?

---

### Post by monkeybrain20122 on 2021-05-26
There are other ways to get inkscape apart from the official repo and ppa. Inkscape itself provides an appimage you can get from its own [webpage]("https://inkscape.org/release/inkscape-1.1/gnulinux/appimage/dl/"). You can allso get it through flatpak.

---

