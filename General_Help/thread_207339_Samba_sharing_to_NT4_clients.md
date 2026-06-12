---
title: "Samba sharing to NT4 clients"
date: 2006-07-01
forum: General Help
---

### Post by rollOver on 2006-07-01
Tried for several hours to get a Windows 2000 machine to backup some recovered files to my new Ubuntu server. Found much help here configuring the samba end but couldn't connect with the right privileges until I discovered elsewhere on the web that NT4 does not support clear-text password negotiation without a registry patch:

------------------------------------

REGEDIT4



;Subject:       Registry file to enable plain text passwords in NT4



[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Rdr\Parameters]

"EnablePlainTextPassword"=dword:00000001

------------------------------------

copy between the lines into a .reg file and apply (or do it manually with regedt32.exe) Hope this help someone else avoid the frustration I did not!

---

