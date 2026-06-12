---
title: "Samba - can't see/connect/ping computers"
date: 2004-11-01
forum: General Help
---

### Post by kaori on 2004-11-01
Hello.

I have 2 computers directly connected, one is Ubuntu and the other is Windows XP. Both the login names and passwords for samba and windows xp are the same, and passwords encrypted = true for smb.conf. I have a public shares set up in /home/kaori/public which is chmodded to 755 and is writeable. The Ubuntu hostname is ubuntu, but I can't ping it from Windows with 'ping ubuntu' or see it in Network connections even though the computers are directly connected. My windows firewall is turned off as well. I can't ping windows from ubuntu either. I've ran testparm on /etc/samba/smb.conf and it doesn't give me any errors, so I'm pretty sure the conf file's syntax is correct. This is my first time using samba so I'm a newbie at it. Thanks very much for any help - Kaori

---

