---
title: "Installed an app from source, howto uninstall?"
date: 2007-07-09
forum: General Help
---

### Post by wconstantine on 2007-07-09
As the topic says. I downloaded a program source code and installed and now I want to undo it  but I can't find it with Synaptic nor remove it with apt-get.

---

### Post by thePsychologist on 2007-07-09
Go into the top directory of the source code and type

[PHP]sudo make uninstall[/PHP]

Most likely that will work. If you don't have the directory any more, download it again.

---

### Post by wconstantine on 2007-07-09
Thanks alot m8. It worked. =)

---

