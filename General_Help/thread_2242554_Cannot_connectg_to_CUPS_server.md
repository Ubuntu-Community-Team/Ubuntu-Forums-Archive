---
title: "Cannot connectg to CUPS server"
date: 2014-09-02
forum: General Help
---

### Post by merlinus on 2014-09-02
I am using 12.04.  Applications/System Tools/Administration/Printing/Server/Settings gives an error (CUPS server error: Not found).  CUPS server is installed.  Here is part of my /etc/samba/smb.conf

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700browsable = yes
guest ok = yes

Also, even when using the app as root, I cannot delete a no-longer-existing printer.

The printer itself works fine.

---

