---
title: "How do I share files with Windows Millenium Edition?"
date: 2007-05-23
forum: General Help
---

### Post by floke on 2007-05-23
Hi,

Title of the thread says it all really. I want to set up sharing between Feisty (laptop) and ME (desktop), but have read that Samba will only work with XP+.

Any suggestions would be much appreciated.

Thanks.

---

### Post by fanatik on 2007-05-24
have you tried Samba?

from the "man samba" page:

smbd(8)
              The smbd daemon provides the file  and  print  services  to  SMB
              clients,  such  as  Windows 95/98, Windows NT, Windows for Work&#8208;
              groups or LanManager. The configuration file for this daemon  is
              described in smb.conf(5)

I'd *think* it would include win ME in that...

Give it a go and let us know how you get on, or post again if you don't know what to do...

---

### Post by ruy_lopez on 2007-05-24
You can try and set up sharing on the Windows box, by choosing a folder and configuring its sharing properties. Then see if you can find it with the Ubuntu network browser, which is accessed from "Places-->Network."

---

### Post by floke on 2007-05-24
Cheers dudes,

Will try these and post back about how it went. Might be a few days though, its not my PC I'm trying to set up so I don't have access to it regularly.

---

