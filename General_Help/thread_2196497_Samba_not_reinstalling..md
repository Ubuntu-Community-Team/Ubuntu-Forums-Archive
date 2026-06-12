---
title: "Samba not reinstalling."
date: 2013-12-29
forum: General Help
---

### Post by josh.t.novotny on 2013-12-29
So I wanted to go back to defaults for samba, so I did these commands:


```
sudo apt-get purge samba
sudo apt-get purge samba-common
sudo rm -rf /etc/samba/ /etc/default/samba
sudo apt-get install samba
```


I right click on my downloads folder and go to "sharing options." The windows closes and says Ubuntu has experienced an error. Sharing options no longer an option, Restarted, same thing.

What happened?

---

### Post by bab1 on 2013-12-29
> **josh.t.novotny said:**
> So I wanted to go back to defaults for samba, so I did these commands:


```
sudo apt-get purge samba
sudo apt-get purge samba-common
sudo rm -rf /etc/samba/ /etc/default/samba
sudo apt-get install samba
```


I right click on my downloads folder and go to "sharing options." The windows closes and says Ubuntu has experienced an error. Sharing options no longer an option, Restarted, same thing.

What happened?
You removed the samba client and its hooks to install the Samba server.  Without the package samba-common the OS has no idea how to share folders.

There is no reason to purge Samba to get back to the defaults.  EVERYTHING is configured in the /etc/samba/smb.conf file for both the client and server.  

Install samba-common and see if it then works for you.  If you have problems post them here before you start removing things.

---

