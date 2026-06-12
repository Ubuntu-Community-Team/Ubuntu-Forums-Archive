---
title: "File sharing: Ubuntu and Windows XP"
date: 2006-09-10
forum: General Help
---

### Post by blueopal on 2006-09-10
I had trouble with SAMBA on Ubuntu (connecting to Ubuntu shares from a Windows XP machine) until I understood why it was always asking for authentication: SAMBA has its own set of users (duh!). I followed this process:

Install SAMBA (use Synaptic Package Manager)
-use WINS (not set by default)

Add folder shares and set permissions (use File Browser)

Add SAMBA user(s)
You will have to add a user like this for each user account you want to connect to this SAMBA domain server. For example:
1) From a terminal session, add a linux user tom:
    sudo useradd tom -m -G users
2) Then, add the linux user tom to the SAMBA password database:
    sudo smbpasswd -a tom

Nothing worked until I completed this last step.

---

