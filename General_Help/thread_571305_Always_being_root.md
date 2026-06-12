---
title: "Always being root"
date: 2007-10-09
forum: General Help
---

### Post by Woet on 2007-10-09
Hello,

I want to have root permissions for everything, as soon as i log in.
Dont warn me about security issues, or whatever.
If virusses format my entire harddisk, its fine with me.. i dont care.

I tried to login with root at the login window, but thats impossible. How can i make it possible, OR how do i give myself root permissions?

Regards,
Wouter van Eekelen

---

### Post by Sef on 2007-10-09
> I want to have root permissions for everything, as soon as i log in.

Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo").

> Dont warn me about security issues, or whatever.
If virusses format my entire harddisk, its fine with me.. i dont care.


You don't have to worry about viruses:  just being hacked and used to send spam, or have illegal images or software downloaded to your computer.

---

### Post by dabl on 2007-10-09
Boot "recovery mode", login with your password, and ```
startx
```

Plan on re-installing everything in 3 or 4 days, when your system is borked up beyond all recovery.  :lolflag:

---

### Post by Woet on 2007-10-09
Well, i dont see any way to login as a root, and staying logged in as a root.

I want to be able to DELETE any directory on my entire harddisk, and not via terminal, but just via the file browser.

---

### Post by thirddeep on 2007-10-09
!!! WARNING !!!
THIS IS BAD (tm)
!!! WARNING !!!

Try System -> Administration -> Login Window -> Security -> Allow local system administrator login.

You are warned :-)

Thd.

---

### Post by dabl on 2007-10-09
From your normal user session in Ubuntu, open the console window and issue ```
gksu nautilus
``` to launch your file manager with Super User power.  Then you can delete whatever you wish, from wherever you wish. :)

---

### Post by Woet on 2007-10-09
Thanks thirddeep ! :)

---

