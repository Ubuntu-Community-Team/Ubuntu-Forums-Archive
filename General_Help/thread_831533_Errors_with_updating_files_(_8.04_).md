---
title: "Errors with updating files ( 8.04 )"
date: 2008-06-16
forum: General Help
---

### Post by Simple512 on 2008-06-16
Ubuntu tells me i have 37 updates and i click install updates and i instantly get this error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


now I go into terminal and type in exactly this ( dpkg --configure -a ) and it returns this message 

dpkg: requested operation requires superuser privilege

please help.

=]

---

### Post by ibutho on 2008-06-16
You have to run
```
sudo dpkg --configure -a
```

---

### Post by Simple512 on 2008-06-16
So sudo allows me to get into superuser privilege mode ?

---

### Post by ibutho on 2008-06-17
> **Simple512 said:**
> So sudo allows me to get into superuser privilege mode ?

On Ubuntu yes. On other distros you may have to switch to root first by running the su command. If you don't want to switch to root first, you can use "su -c sommecommands" and enter the root password when prompted.

---

### Post by crutch on 2008-06-17
I've got the same problem with updating, except I can't get the command given to work (I am using sudo) Could you let me know if this works for you. In my case I think I may have interupted the update manager last time I used it.

---

### Post by rainwalker on 2008-06-17
What about the command isn't working?
Just a note, it will ask for your password but when you type it in nothing will show up; it's just a security thing

---

### Post by crutch on 2008-06-17
I seem to have fixed my problem with the help of linuxquestions ([http://www.linuxquestions.org/questions/ubuntu-63/dpkg-configure-a-error-361965/](http://www.linuxquestions.org/questions/ubuntu-63/dpkg-configure-a-error-361965/))

Seems it was some temporary files that were left behind, posibly if I interupted update manager last time I was using it.

The linuxquestions thread may be helpful to anyone else having problems with this.

---

