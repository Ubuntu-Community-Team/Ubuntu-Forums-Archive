---
title: "Disk mounting delay issue"
date: 2020-11-16
forum: General Help
---

### Post by michael351 on 2020-11-16
I have a network drive when not in use goes into standby mode. I access it as an SMB share.
Occasionally, when I boot up my Ubuntu desktop, and if the drive is in standby, the drive won't mount and Ubuntu proceeds with out it.
This happens only occasionally, but is annoying. 

Is there syntax I can use in my fstab entry (see below) to pause/wait the ubuntu mount process until my network drive spools up and comes online to the network. 

/etc/fstab entry:

//192.168.1.75/Public /media/Public cifs uid=cust01,nofail,credentials=/home/user/.smbcredentials,iocharset=utf8 0 0

---

### Post by TheFu on 2020-11-16
I use **autofs** for *sometimes unavailable* network storage.

There's a how-to easily found "ubuntu autofs"

---

