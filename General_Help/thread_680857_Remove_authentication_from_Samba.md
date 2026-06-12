---
title: "Remove authentication from Samba"
date: 2008-01-28
forum: General Help
---

### Post by pepsi_max2k on 2008-01-28
I just got Samba running to share a folder, then went to access it from another PC and it asked for a username/password. I know I can set these using smbpasswd but how can I remove the authentication completely so I don't ever need to enter a user/password? Thanks.

---

### Post by luisromangz on 2008-01-28
In the file /etc/samba/smb.conf, set

security = share

---

### Post by pheadm on 2008-01-29
Thanks Luis. I also had the same problem and this answers it. Am just a newbie with Linux/Ubuntu, my first time to dip my fingers into this. Always have been a windows user and nothing else (correction, had some light training with AIX 15 years ago :).

---

