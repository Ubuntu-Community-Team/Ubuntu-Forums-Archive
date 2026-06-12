---
title: "Ruh-Roh...not good"
date: 2008-07-07
forum: General Help
---

### Post by ianoreo on 2008-07-07
Okay so all of the sudden when I logon i got this error that said I needed to switch my permissions on the /home folder to 644. So I enter into Ubuntu and open terminal and type sudo chmod 644 /home

Now I am suddenly locked out from opening any programs. Is there anyway I can force open terminal so I can fix the permissions?


Ian

EDIT: I've also noticed that I cannot login to the computer.

---

### Post by kuja on 2008-07-07
Well, what I would do would be this:

```

find /home/yourusername -type d -execdir chmod -R 744 {} \+
find /home/yourusername -type f -execdir chmod -R 644 {} \+

```

---

### Post by rossjman1 on 2008-07-07
Can you log in as root?

---

### Post by timcredible on 2008-07-07
the solution is going to be to put your UID back to what it was.  the chmod didn't change ownership, just permissions, and you need to own your  home directory in order to be able to open programs because they all want to store some info in your home drive.  so, do a ```
ls -l /home
``` and see what UID owns your directory, and make your UID the same.  that requires changing /etc/passwd and /etc/shadow, you'll want to do a search on how to do this safely, hopefully you can login as root and do it with 'users and groups' menu option.

---

### Post by ianoreo on 2008-07-07
Failsafe GNOME or Terminal?

EDIT: Failsafe term on the ls -l /home command said:

```
drwr--r-- 44 ianoreo ianoreo 4096 2008-07-07 11:58 ianoreo
```

---

### Post by ianoreo on 2008-07-07
I don't really know what to do now?

---

### Post by txcrackers on 2008-07-08
kuja's got the right stuff - start in "Safe mode", run those commands, and then you should be able to proceed normally.

---

