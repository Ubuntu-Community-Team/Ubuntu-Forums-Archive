---
title: "how to install printers.conf"
date: 2015-07-26
forum: General Help
---

### Post by mukesh_kumar on 2015-07-26
how to install printers.conf in /etc/cups

please help 


Thanks

---

### Post by Bucky Ball on 2015-07-26
*Thread moved to **General Help**. *

Why are you wanting to? Please give full details of what you're trying to do and more information, thanks. If you are trying to install a printer, make/model please and the release and flavour of Ubuntu you are using.

---

### Post by efflandt on 2015-07-26
To add a printer, you typically do that from System Settings > Printers, or [http://localhost:631/admin](http://localhost:631/admin) in a web browser.

But for the latter (URL) I think you need to be in (or add yourself to) **lpadmin** group:```
efflandt@XPS-8100-1404:~$ groups
efflandt adm cdrom sudo dip plugdev lpadmin sambashare
```If you need to add yourself to lpadmin group you are supposed to use **vigr** or **vipw** to edit **/etc/group** (which locks the file while editing, assuming you know how to use vi), but as the only user on the system, I have edited it with **sudo nano /etc/group**. You just add your username after the ":" in the lpadmin line, or if more than one user it is a comma separated list like this```
lpadmin:x:108:efflandt,deffland
```

---

