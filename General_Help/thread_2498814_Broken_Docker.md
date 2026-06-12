---
title: "Broken Docker"
date: 2024-06-28
forum: General Help
---

### Post by BigYellowDog on 2024-06-28
Running server 22.04.4 LTS.  After the recent docker update, I can no longer access any of my containers.  

The two containers that I am running I access via a web page, that does not work.

[COLOR=#008000]*docker container ls -a*[/COLOR] has a status of [COLOR=#ff0000]Exited (128) 16 hours ago[/COLOR] for both containers

I'm guessing the last update broke something

---

### Post by BigYellowDog on 2024-06-28
A reboot fixed it.

---

