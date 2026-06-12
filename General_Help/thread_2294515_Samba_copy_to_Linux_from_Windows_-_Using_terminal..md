---
title: "Samba copy to Linux from Windows - Using terminal."
date: 2015-09-11
forum: General Help
---

### Post by aaron27 on 2015-09-11
I can access a windows share in Samba on my linux install (smb) but i now want to copy the file to my Linux machine. I have setup a local share on the linux machine and edited the smb.conf file to allow access however i cannot find the command to copy the file. I am using 12.04 with no GUI installed so need the instructions strictly in terminal format please.

Probably quite a basic question but not something I am familiar with at all.

---

### Post by SeijiSensei on 2015-09-11
At the terminal, run the command "man smbget" to see the manual page for the **smbget** program.  It's designed to retrieve files from an SMB share the same way wget retrieves files from HTTP sites.

---

