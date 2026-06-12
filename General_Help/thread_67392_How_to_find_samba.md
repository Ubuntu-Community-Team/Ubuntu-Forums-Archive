---
title: "How to find samba"
date: 2005-09-20
forum: General Help
---

### Post by docmanny on 2005-09-20
I know this is a dumb question. 

I want to use samba, but I can't find it!

I have /etc/samba/smb.conf

But i can't find samba or smb in any of the /etc/init.d or /etc/rcX.d directories.

---

### Post by sundancer on 2005-09-20
Did you install the package 'samba'? 
In a default install of ubuntu, only 'samba-client' is installed.

If you installed it before, you should try
```
sudo apt-get install --reinstall samba
```.

Good luck :)

---

