---
title: "GConf Error"
date: 2007-05-20
forum: General Help
---

### Post by TannerLD on 2007-05-20
Hi all,

I tried to start Nautilus and I got this error:

```

GConf error: Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILUE:1.0

All further errors shown only on terminal.

```

In another error box I have:

```

Add error occurred while loading or saving configuration information for Nautilus. Some of your configuration settings may not work properly.

Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0

```

On the terminal is says this a LOT of times:
```

(nautilus:16604): Eel-WARNING **: GConf error:
  Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0

```

Anyone know how to fix this?

Thanks
-Tanner

---

### Post by bapoumba on 2007-05-20
Hello :)

Googled your error, that is the only fix I found:
[http://mail.gnome.org/archives/nautilus-list/2002-June/msg00220.html]("http://mail.gnome.org/archives/nautilus-list/2002-June/msg00220.html")
You can read the previous mails, he was logged from two different computer when this happened.

In any case, your could create another user (**sudo adduser test**, assuming "test" is your new user) and log in "test" session. If "test" is OK, then your regular user has a prob with conf files (.gconf, .gnome, .gnome2, .nautilus ...). You can rename them one by one, log out and log back in, to find which one is giving you this error. Be aware that you will revert to default settings, thus default desktop theme and such.

---

### Post by TannerLD on 2007-05-20
Hmm...

I decided to do a restart (hey - why not) and I'm not getting the error anymore....strange.

-Tanner

---

### Post by bapoumba on 2007-05-21
> **TannerLD said:**
> Hmm...

I decided to do a restart (hey - why not) and I'm not getting the error anymore....strange.

-Tanner
Probably some temp file go a reset and all is nice again :)

---

