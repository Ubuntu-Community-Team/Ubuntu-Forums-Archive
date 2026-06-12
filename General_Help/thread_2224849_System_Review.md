---
title: "System Review"
date: 2014-05-18
forum: General Help
---

### Post by Rakesh_vijayan on 2014-05-18
Hi every body 


Let me know dear friends how I can view the installed and deleted packeges ,and a torrent log with what they access with the torrent , is it possible to view the past thing now .If it possible please help me because it is an urgent requirement to me for review a particular ubuntu system 


Thanks

---

### Post by dragonfly41 on 2014-05-18
From Ubuntu Software Centre .. install Synaptic Package Manager .. then select various package filters in left sidebar.

---

### Post by deadflowr on 2014-05-18
You can view package info, in Ubuntu Software Center > History.
I don't know what you by the second thing about torrents, though.

---

### Post by Rakesh_vijayan on 2014-05-18
basically I need to review that is it any torrent uses in that audit system ,if it usess the torrent which file that uses and also view how much bandwidth uses this system like a firewall do so ?

---

### Post by Rakesh_vijayan on 2014-05-18
> **deadflowr said:**
> You can view package info, in Ubuntu Software Center > History.
I don't know what you by the second thing about torrents, though.

is it ubuntu s/w center display if it use apt-get purge  package command

---

### Post by deadflowr on 2014-05-18
> **Rakesh_vijayan said:**
> is it ubuntu s/w center display if it use apt-get purge  package command

Don't know.
But the folder 
```
/var/log/apt/
```
should have a file called history.log, and possibly a few archive folders called history.log.gz, or something.
That should show ALL apt-get commands for upgrade, install, purge, and removal you have done.

---

### Post by Rakesh_vijayan on 2014-05-19
I Think There is no option for the audit the deleted history of torrent  files

---

### Post by dragonfly41 on 2014-05-19
Does this terminal command yield any useful information ..

$ history > ~/history.txt

---

