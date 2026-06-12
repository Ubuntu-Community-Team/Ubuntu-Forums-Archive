---
title: "Upgraded to 8.04LTS, lost samba shares"
date: 2008-04-22
forum: General Help
---

### Post by mattholland on 2008-04-22
Hi guys, 
I upgraded from 6.06LTS to 8.04LTS today - when prompted, I chose to keep the existing smb.conf file.

I have a number of shares set up on the ubuntu machine, as follows

\media - public access
\shared - public access
\web - private (access control by user + pass)
\home - private (access control by user + pass)

With 6.06, the user name and password were the same for ubuntu as the windows client machines, meaning username and password were passed my MS machine to ubuntu. 

Now I've installed 8.04 i am unable to access \web or \home from my windows machine. An error message saying "access is denied", and "incorrect username / password".

Does anybody have any idea why upgrading would cause this problem, and how I can correct it?

---

### Post by Iowan on 2008-04-22
I wonder if the **smbpasswd** file got replaced...
Try adding your user/password back in...
OR... they haven't been added to the system users.

---

### Post by Joeb454 on 2008-04-22
It is possible, if it didn't ask about that file specifically then it's more likely than possible :(

You could try reconfiguring samba?

---

### Post by Joeb454 on 2008-04-22
It is possible, if it didn't ask about that file specifically then it's more likely than possible :(

You could try reconfiguring samba?

---

