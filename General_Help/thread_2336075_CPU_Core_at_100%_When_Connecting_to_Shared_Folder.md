---
title: "CPU Core at 100% When Connecting to Shared Folder"
date: 2016-09-04
forum: General Help
---

### Post by uRock on 2016-09-04
Has anyone else noticed or had a problem with having one CPU core go to 100% when trying to connect to a local shared folder on another ubuntu system? 

When I look in System Monitor or **htop**, I see **gvfsd-smb-browse** is the culprit running up the CPU.

When this happens, which seems to be 90% of the attempts, the connection with the shared folder usually never happens.

Edit: I just attempted to follow this workaround, [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1409032/comments/29](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1409032/comments/29), but there isn't a Samba folder in /etc and searching for smb.conf doesn't return anything.

---

### Post by uRock on 2016-09-04
It seems there was an issue with DNS. Once I configured a static DNS on this machine the problem went away.

---

