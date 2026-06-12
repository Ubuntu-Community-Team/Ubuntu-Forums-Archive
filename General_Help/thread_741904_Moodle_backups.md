---
title: "Moodle backups"
date: 2008-04-01
forum: General Help
---

### Post by balalusesa on 2008-04-01
I am trying to back up my moodle system but whenever I put the path to another computer I always get the message incorrect path. I usually write the path as "/10.20.41.12/var/moodlebackup"  where by the ip address 10.20.41.12 is of the other PC on the network

---

### Post by justleen on 2008-04-01
try to find the other computer on the network, via the network browser. then copy and paste it trough the GUI.

From the commandline you cannot simply cp file /serverip/path
you either have to mount the destination as samba or NFS. Another option would be to ftp or copy over ssh..

---

