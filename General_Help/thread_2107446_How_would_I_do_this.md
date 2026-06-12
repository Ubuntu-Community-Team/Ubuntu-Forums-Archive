---
title: "How would I do this?"
date: 2013-01-21
forum: General Help
---

### Post by dmallion on 2013-01-21
so I have a script or something that makes files in /opt/ however I have insufficient permissions. How could I fake it to think /opt/ is in my home like /home/user/opt/ ?

---

### Post by ManamiVixen on 2013-01-21
Please tell us your Ubuntu version and what you are trying to do exactly. That can help alot, thanks! :)

---

### Post by Lightning Dragon on 2013-01-21
Hello,

If all you are trying to do is gain permissions in Ubuntu 12.04 (you need to give us more details), open the Terminal and type;

gksudo nautilus (which I suggest using)

Gaining root permission would allow you to create, delete, move, and copy files.

---

### Post by pissedoffdude on 2013-01-21
One way to allow write access to /opt is to run the script with sudo.  But before doing so, let us know what the script is supposed to do.  If it's for an app, chances are there's another way to install it.

If you want, you can post the script here.

---

### Post by deadflowr on 2013-01-22
> **dmallion said:**
> so I have a script or something that makes files in /opt/ however I have insufficient permissions. How could I fake it to think /opt/ is in my home like /home/user/opt/ ?

Rewrite the script.
A script is only going to do what is was written to do.
If it's written to install files into /opt then that's what it'll do.
The only way to 'fake it' is going to be to re-write it.

---

### Post by dmallion on 2013-01-23
Sorry I was away for a bit. Thanks for all the help guys however I figured out that I could use chroot. Problem solved:D

---

