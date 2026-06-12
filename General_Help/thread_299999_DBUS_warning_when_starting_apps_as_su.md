---
title: "DBUS warning when starting apps as su"
date: 2006-11-15
forum: General Help
---

### Post by FooSoft on 2006-11-15
I'm running into a strange problem where when I execute an application using sudo, I get the following warning in console:

```

foosoft@wintermute:~$ sudo gedit
Password:

(gedit:5240): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. 
Possible causes include: the remote application did not send a reply, the message bus security policy 
blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

```

This happens for pretty much anything... Does anyone have an idea as to what could be causing this? This is on a clean install of Ubuntu 6.10 (amd64).

---

### Post by nikhilk on 2006-11-15
You should generally run graphical applications which require root permission with gksudo and not just sudo.
Try
```
gksudo gedit
```

---

### Post by FooSoft on 2006-11-15
> **nikhilk said:**
> You should generally run graphical applications which require root permission with gksudo and not just sudo.
Try
```
gksudo gedit
```

Yes, I've tried that as well. Unfortunately I still have the same problem.

---

### Post by morganGDFP on 2007-03-11
> I'm running into a strange problem where when I execute an application using sud
I get the same thing..But not on all applications, though...Did yoy find out any solution for your problem?

---

