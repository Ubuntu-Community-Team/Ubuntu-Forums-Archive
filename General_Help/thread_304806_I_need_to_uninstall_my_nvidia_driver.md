---
title: "I need to uninstall my nvidia driver"
date: 2006-11-22
forum: General Help
---

### Post by onesojourner on 2006-11-22
I screwed my nvidia drivers up pretty good, I tried to intall the newest version over an old version and now stuff is screwed up. how can a uninstall them and then reinstall?

---

### Post by renzokuken on 2006-11-22
go here

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

and go down to the bit titled "How to Uninstall the Driver"

this can be done from a terminal so no need to boot into any desktop

---

### Post by onesojourner on 2006-11-22
ok I did that, now I have a new problem. after I reboot my normal login screen comes up and I login but it never boots. the login goes away but nothing pops up loading the rest of the gui. it just sits there on the tan screen with a cursor. I can hit ctrl alt delete and get the system monitor.

---

### Post by renzokuken on 2006-11-22
did u edit your xorg.conf and select a new driver, preferably "vesa"

or you can do it with a command like

sudo dpkg-reconfigure xorg-server

i'd check if thats right though, but something like that does it

---

