---
title: "problem mapping drives from kubuntu.."
date: 2008-02-16
forum: General Help
---

### Post by Mia_tech on 2008-02-16
after installing samba on my kubuntu box, I created two shares which I can access from my windows xp machine, but the problem is if I access the share using ip address it works ok, but if I try to map the drive using the server name, it prompt me for a username and password... am I missing something in the smb.conf file...here's how I setup the share

 [Share]
  comment = Share forlder
  path = /media/usbdisk/share
  guest ok = yes
  writable = yes
  browsable = yes

thanks

---

