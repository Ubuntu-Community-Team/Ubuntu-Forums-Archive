---
title: "Running a program all the time in sudo"
date: 2007-06-04
forum: General Help
---

### Post by Darkjasper on 2007-06-04
Alright I need to run Thunderbird with the sudo command so that it has access to the domains for webmail. I was wondering if there was a fix so that it would always be in admin mode. I have tried putting sudo in-front of the command in the launcher but that fails after awhile. Any thoughts?

---

### Post by NumberOne on 2007-06-04
Try using gksu in front of the program command.  "gksu thunderbird"

---

### Post by Darkjasper on 2007-06-04
That just seemed to reinstall and I would still have to enter my pass every time I run it. Thanks though.

---

### Post by steeleyuk on 2007-06-04
I've no idea if this will work as expected but try:

gksu -w <program_name>

The password box will pop up and will give you the option to remember the password for the session or store it in the keyring.

---

