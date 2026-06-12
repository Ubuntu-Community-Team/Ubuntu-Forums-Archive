---
title: "windows domain membership"
date: 2008-03-25
forum: General Help
---

### Post by fouadk on 2008-03-25
hi everyone....

i have successfully joined my ubuntu machine to a windows domain...

my problem is that the administrator account of that domain can't access my shares(music, files....)

the administrator account should have unlimited access to any machine...

how to make ubuntu follow this policy ???

please help..

thanks in advance...

---

### Post by cmnorton on 2008-03-25
Your Ubuntu system joining the Windows domain is a start, but not an end. You use domain login membership for sharing Windows-defined printers, as one example. However, if you want the Windows domain administrator (or any Windows user) to have access to all or some of your files, you need to share those files or printers. The best way to do that is samba.

Look at /etc/samba/smb.conf and search these forums for smb.conf editing hints.

There is a way in Samba to map Windows users to one or more Linux users. Or, you can create a Linux account for each Windows account that needs access to files on your Windows system.

---

