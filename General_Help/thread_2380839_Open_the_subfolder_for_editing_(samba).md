---
title: "Open the subfolder for editing (samba)"
date: 2017-12-22
forum: General Help
---

### Post by skifua on 2017-12-22
I have a Dropbox. And one folder in it I made opened to network area (only for read). One subfolder must be for writining. My settings in Samba are:

[KOMORA]
comment = dropbox share
read only = no
locking = yes
path = /home/vchutel/Dropbox/KOMORA
guest ok = yes
writable = no
force user = vchutel

[KONTROL]
comment = dropbox share
read only = no
locking = yes
path = /home/vchutel/Dropbox/KOMORA/KONTROL
guest ok = yes
writable = yes
force user = vchutel


but in KONTROL users also can only read data, not editing. When I deleted permissing for KOMORA then I can editing then content of KONTROL (from network). 
p.s. english is not ma native.

---

### Post by skifua on 2017-12-25
any ideas?

---

### Post by deadflowr on 2017-12-25
*Thread moved to **General Help***

I think the issue is you've already set the top directory as read-only, so any subsequent directories within that directory will also be read-only.
I'm not sure if samba can work around that.

---

### Post by skifua on 2017-12-26
> **deadflowr said:**
> *Thread moved to **General Help***

I think the issue is you've already set the top directory as read-only, so any subsequent directories within that directory will also be read-only.
I'm not sure if samba can work around that.
What I can to do? - users can read all folders in KOMORA but only one can editing. I don't want to open permissions to all reading-folders, because they can be modify (from me).

---

