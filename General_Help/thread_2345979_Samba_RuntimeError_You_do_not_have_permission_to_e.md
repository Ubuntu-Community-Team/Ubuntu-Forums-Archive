---
title: "Samba RuntimeError: You do not have permission to execute /usr/bin/pdbedit"
date: 2016-12-09
forum: General Help
---

### Post by new2ubuntu on 2016-12-09
I installed [COLOR="#6666FF"]samba[/COLOR] and [COLOR="#6666FF"]system-config-samba[/COLOR] as always in Ubuntu 16.04 but when I went to launch it I get:
[FONT=Lucida Console][COLOR="#FF0000"]Samba RuntimeError: You do not have permission to execute /usr/bin/pdbedit[/COLOR][/FONT]

I check permissions, this is not true. Puzzled, I do a little more digging. 
Someone said it needs to run as root, so I 
[FONT=Lucida Console][COLOR="#0000FF"]gksu system-config-samba[/COLOR][/FONT]
 
and then you get:
[COLOR="#FF0000"]SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory[/COLOR]

puzzled, I create an empty one;
[FONT=Lucida Console][COLOR="#0000CD"]sudo touch /etc/libuser.conf[/COLOR][/FONT]

Then I fire it up, it runs fine. Thought this might help someone who wants to use the system-config-samba to setup their samba shares. It really should do this if there is none when the package installs...

Eric

---

### Post by christianhorn on 2017-10-03
THANKS!

**sudo touch /etc/libuser.conf**

---

