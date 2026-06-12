---
title: "Samba and Windows 2003, Write Privs?"
date: 2007-02-02
forum: General Help
---

### Post by Grax on 2007-02-02
Running a Ubuntu 6.06 Server

I'm trying to mount a Windows 2003 share and can only get read permissions. The command I've tried is below, which is run from a bash script which passes all the needed information.

mount -t cifs $smbpath $smbmount -o username=$smbuser,workgroup=$smbdomain,password=$smbpass

I've also tried:

mount -t cifs $smbpath $smbmount -o username=$smbuser,workgroup=$smbdomain,password=$smbpass,iocharset=utf8,file_mode=0777,dir_mode=0777

Both of these mount the share without problems, however I only have read access. How can I get read/write access?

This is only an issue with W2K3, I've tried using a W2K Server and XP machine and both mount with read/write privs.

Thanks in Advance,

Andrew

---

### Post by Spano on 2007-02-02
sorry

---

