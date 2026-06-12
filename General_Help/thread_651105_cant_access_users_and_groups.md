---
title: "cant access users and groups"
date: 2007-12-27
forum: General Help
---

### Post by sandclock on 2007-12-27
Hi
have a fresh install of Ubuntu 7.0.4 and i want to enable root user. 
i tried to access system-> administation --> users and groups but the window doesnt open it says starting users and groups and then disappears. 
can any one suggest me solution?
Regards
nik

---

### Post by jken146 on 2007-12-27
That is a bit strange.  Are you doing this as an admin user (if you are the user created during the install then the answer is yes)?

To be honest, you don't need to enable the root account.  It's much easier to type ```
sudo -i
``` and enter your password to get temporary super user privileges.  It's *much* safer too.  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Try ```
gksudo users-admin
```

---

### Post by sandclock on 2007-12-27
Hi
thanks for suggestion i need to login as root fro gui mode to install some software and not from terminal.
facts
P4 3ghz
1 gb ram
80 gb hdd
using entire harddisk option when installing
thanks again
Regards
Nik

---

### Post by jken146 on 2007-12-27
Did you get Users and Groups to appear?

If all you need to do is install something, there is no need to enable the root account.  Just use Synaptic to install things with a GUI.

---

### Post by bodhi.zazen on 2007-12-27
> **sandclock said:**
> Hi
thanks for suggestion i need to login as root fro gui mode to install some software and not from terminal.
facts
P4 3ghz
1 gb ram
80 gb hdd
using entire harddisk option when installing
thanks again
Regards
Nik

Ubuntu uses sudo ...

Go to a console (Ctrl-alt-F1 or F2)

Log in

enter : ```
sudo -i
```

Enter your log in password when asked and you will now be root in a console (rather then a terminal).

If you need to stop X :

```
/etc/init,d/gdm stop
```

change stop to start to re-start GDM

===========

If you really want to set a root password,

```
sudo passwd
```

but it is really not necessary.

To un-do this :

```
sudo passwd -L root
```

---

### Post by sandclock on 2007-12-28
hi thanks it worked on command prompt but i still cant open users and groups from gnome any ideas wats wrong here?
thanks and regards
Nik

---

### Post by sandclock on 2007-12-28
I created groups from command prompt as described about but I can not login using those from login screen. and worst thing is i still dont get "users and groups" interface from system--> administration--> users and groups.
i am fighting with this for last week with little success. any help is really appriciated
Regards
Nik

---

### Post by jken146 on 2007-12-28
Did you do what I suggested, that is, ```
gksu users-admin
```?

---

### Post by sandclock on 2007-12-28
> **jken146 said:**
> Did you do what I suggested, that is, ```
gksu users-admin
```?

Hi yes i tried that one
---> it asked for me password i gave password. it tried to open users and groups (starting users and groups message) but the nothing happened
Regards
Nik

---

### Post by sandclock on 2007-12-28
any ideas anyone?:( i am really frustrated and desparate here 
Regards
Nik

---

