---
title: "samba - new folder creation issue"
date: 2018-10-16
forum: General Help
---

### Post by sniper8752 on 2018-10-16
I notice when I create a new folder, it creates 4.  Why is this happening?

---

### Post by TheFu on 2018-10-17
Don't know.  Not happening here. Perhaps if you explain exactly what is happening, how you are creating directories and which tools are used on both the client and server side, someone could reproduce it?  Versions for everything are probably needed as well.

Or not.

---

### Post by sniper8752 on 2018-10-18
I create the directory in windows by right-clicking, and then click New Folder.
Samba is running on the server side.  Not sure what you mean by what's on the client side.  It's just windows 10.  
When you say 'everything', can you be more specific?

---

### Post by TheFu on 2018-10-18
You didn't mention Windows before, so I didn't assume it.  There are many different ways to create folders from different OSes.
I don't have Win10, so can't attempt to reproduce the issue, sorry.  I can confirm that on Samba v 2:4.3.11+dfsg-0ubuntu0.16.04.17 running on a 16.04.5 server, neither Win7 Explorer nor Ubuntu Caja on 16.04 (v1.12.7-1ubuntu0.1) show the issue.
Also, using smbclient from 14.04 and 16.04 do not show this issue.

At this point, more data gathering is needed.  If you can run **testparm** on the server and post those results and grab the relevant logs from /var/log/samba/ showing the issue only when the 4 folders are created, that would be helpful.  If you can reproduce the issue using a shell client for samba with lots of "verbosity" enabled, then we'd know it wasn't just Windows10.

Also, is the server fully patched?  Which OS, which release, which samba version?

Hopefully, my details will help you gather similar details.

---

