---
title: "Audacity: empty menus and dialogs"
date: 2006-12-28
forum: General Help
---

### Post by Prism on 2006-12-28
Hi there,

When I start audacity, the sound recorder, the program menus aren't shown and I can see only dots. Clicking on them opens a menu, which contains dots again.

It happens with the Open/Save File dialogs as well. I can see the folder's icons, but not the names.

A screenshot is attached. It will probably explain it better than me. :)

Thanks in advance :)

---

### Post by KenSentMe on 2006-12-28
Have you installed the program through Synaptic or apt, or did you do it manually? Has the problem been there since you installed Audacity, or later?

---

### Post by Prism on 2006-12-28
I installed it via synaptic. I can't remember if it has been always - I installed it long time ago but only today I actually needed it.

Meanwhile, I tried to install Quake 3 following [this guide]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3"). The file linuxq3apoint-1.32b-3.x86.run opens dialog boxes which act the same.

I think it some kind of a problem with one of the graphical toolkit, like gtk or qt. Both are working fine, so it isn't any of them.

---

### Post by Prism on 2006-12-29
Anyone please?

---

### Post by KenSentMe on 2006-12-30
I've found something related to your problem here: [https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

#

audacity (and other gtk1 applications)
* Problem: No menu text in the english locale, after updating from Dapper. [WWW] Bug #62300
* Workaround: rm ~/.gtkrc-1.2-gnome2 , and make sure xfonts-{100dpi,75dpi,scalable} are installed.

Hope it works for you

---

### Post by Prism on 2007-01-03
There wasn't any .gtkrc directory in my home folder, therefore I couldn't remove it. xfonts100, 75 and scalable are already installed. I re-installed them using Synaptic but problem keeps happenning.

Today I noticed it happens with scorched3d as well. The texts in the game are shown as gibberish.

---

