---
title: "Unable to startx"
date: 2005-04-06
forum: General Help
---

### Post by asimex on 2005-04-06
All,

just installed latest Horay. Trying to to start X, X will start up and immeadiatly close down again.
Error is "Client 5 rejected from local host"
Googling shows a lot of people having the same question, but no usable answer.

Any help appreaciated.

---

### Post by Leif on 2005-04-06
Have you tried switching to a different display driver, ie. nv instead of nvidia, just to check ?

---

### Post by asimex on 2005-04-06
Same results, it fails with the same error.

---

### Post by Leif on 2005-04-06
Can you please tell me the exact versions of the nvidia drivers and xorg you are using ?

---

### Post by alastair on 2005-04-06
Show the X errors from :

/var/log/Xorg.0.log

and the relevant messages from :

/var/log/syslog

---

### Post by asimex on 2005-04-08
[QUOTE=alastair]Show the X errors from :

/var/log/Xorg.0.log

and the relevant messages from :

/var/log/syslog[/QUOTE]
 Fixed it, some screwed up installtion, reinstall solved the issue.

Thanks

---

