---
title: "Window manager gone!"
date: 2006-12-19
forum: General Help
---

### Post by GolerGkA on 2006-12-19
I've just followed [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29") instructions and my window manager is gone! There are applications, there is gnome panel, there is even a menu & firefox that i was able to launch, but no window borders and headers! Even as I restarted Gnome!

Plz, help me... I understand that may be I must post it somewhere else, but "you're my only hope".

**Update**

I don't know why, but after reboot all seems to be fine.
Sorry.

---

### Post by kd7swh on 2006-12-19
The same thing happened to me, 
   "metacity" isn't launching at startup. Even after reboot in my case.

---

### Post by hikaricore on 2006-12-19
try running:

```
metacity --replace&
```

from a terminal (inside of an X session of course).

It seems compiz or beryl is not working properly for you, you may need to abandon using it for the moment to have a functioning desktop.

---

