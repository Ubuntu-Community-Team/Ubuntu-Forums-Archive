---
title: "login as root"
date: 2007-05-23
forum: General Help
---

### Post by atlfalcons866 on 2007-05-23
how do i login as root?

---

### Post by fmz on 2007-05-23
in terminal type su and later put your password

---

### Post by The Squig on 2007-05-23
if you want to log in as root in gnome gor tp System.-> adminitstration -> users and groups. specify a password for your root account. Then go to system -> administration -> login window -> security:  and allow system admins to log in. 

this solution  is not recomended tho.

---

### Post by revilodraw on 2007-05-23
why is this solution not reccomended?

---

### Post by Crafty Kisses on 2007-05-23
> **revilodraw said:**
> why is this solution not reccomended?

I don't think he knows either. ;)

---

### Post by thk on 2007-05-23
```
sudo -i
```

---

### Post by fazavon on 2007-05-23
It is not recommended for the same reason that you do not use the administrator account in windows. If you go to an unprotected site of get a virus it will run ramped because it has the "rights" to do so.

---

### Post by aysiu on 2007-05-23
You never need to log in as root or set a root password in Ubuntu.

Read these links for more details:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by SgtDude on 2007-05-25
> You never need to log in as root or set a root password in Ubuntu.

While I agree that you rarely need to actually assign root a password to get it out of limbo, there are certain circumstances where root needs a password.  For example:  SWAT (Samba Web Administration Tool) will not let anyone but root perform administrative functions.  Now if you can tell me how to use sudo in a web interface, I'll be very impressed.

Anyhoo...

> ...Then go to system -> administration -> login window -> security: and allow system admins to log in. 


does anyone know the command-line approach to this?  I'm building a LiveCD and need to be able to log in to Gnome as root, but I only have command-line access to the LiveCD-to-be (via Reconstructor).

---

### Post by Arisna on 2007-05-25
> **SgtDude said:**
> Now if you can tell me how to use sudo in a web interface, I'll be very impressed

Would this work?

```
gksudo firefox <URL for SWAT>
```

---

### Post by SgtDude on 2007-05-25
Nope, that would run Firefox as your local machine's root.  You would then try to connect to SWAT's web interface, and be asked for a username and password.  Root not having a password, root would not be able to log in.

Nice try, though.

;)

---

### Post by Arisna on 2007-05-25
> **SgtDude said:**
> Nope, that would run Firefox as your local machine's root.  You would then try to connect to SWAT's web interface, and be asked for a username and password.  Root not having a password, root would not be able to log in.

Nice try, though.

;)

>_<

I forgot that people would want to use SWAT on remote machines.

---

