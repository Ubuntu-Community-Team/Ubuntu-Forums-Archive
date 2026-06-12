---
title: "software center not loading in Release:	22.10"
date: 2022-10-21
forum: General Help
---

### Post by longhornlts92 on 2022-10-21
After installing the latest version of Ubuntu 22.10 I installed the minimal install but I don't know if that has anything to do with it.
I don't know how to check for errors on logs kinda a noob so

---

### Post by longhornlts92 on 2022-10-21
if anyone else faces the same problem I just went to the snapcraft help

sudo systemctl restart snapd snapd.socket
sudo systemctl daemon-reload

restarted the system an snap-store works

---

