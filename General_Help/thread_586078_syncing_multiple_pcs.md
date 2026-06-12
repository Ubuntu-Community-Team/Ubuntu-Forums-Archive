---
title: "syncing multiple pcs"
date: 2007-10-21
forum: General Help
---

### Post by mperedithe on 2007-10-21
Does anyone know of a way to synchronize multiple pc's.  I have a Gateway laptop with Ubuntu 6.06LTS and an HP desktop with Ubuntu 6.10 and I'd like to have them synced so that if I have trouble with one the other can act as a back and so that I go from one to the other and feel like I'm using the same PC.

---

### Post by bit4 on 2007-10-22
Setting up a cron job to run rsync is the first thing that comes to mind. The down side is that this will not keep them in sync continuously. If one fails, you will lose the work you did since the last rsync run.

---

