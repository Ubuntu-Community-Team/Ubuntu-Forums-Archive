---
title: "Citrix Receiver + Ubuntu LTS"
date: 2015-01-05
forum: General Help
---

### Post by Nikos_Skalis on 2015-01-05
Dear All,

I followed the guidelines as described here [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo) on how to make the Citrix Receiver working.
But, when I choose a Citrix app to open, what I get is the following message :

*Cannot find the file : (/home/nskalis/.ICAClient/wfclient.ini). Please check your installation, or contact your help desk.*

The file in question though exists :

[I]ls -salt /home/nskalis/.ICAClient/wfclient.ini
4 -rw------- 1 root root 1266 Jan  5 18:54 /home/nskalis/.ICAClient/wfclient.ini[/I]

Any ideas ?

---

### Post by wyliecoyoteuk on 2015-01-05
unless the citrix app is running as root, you probably need to take ownership, or to make it group or world readable.
At the moment, only root has read/write access to it.

---

