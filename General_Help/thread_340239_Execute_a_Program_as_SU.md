---
title: "Execute a Program as SU?"
date: 2007-01-16
forum: General Help
---

### Post by kamlapati on 2007-01-16
I installed wlassistant to help with my wireless, but when I run it I get an error message saying I can only run it as su.

How do I modify the gnome menu to automatically request the root password?

---

### Post by ardchoille42 on 2007-01-16
> **kamlapati said:**
> I installed wlassistant to help with my wireless, but when I run it I get an error message saying I can only run it as su.

How do I modify the gnome menu to automatically request the root password?

You can run command line apps with root permissions with:

[COLOR="Red"]sudo appname[/COLOR]

You can also run GUI apps with root permissions from the terminal with:

[COLOR="Red"]gksudo appname[/COLOR]

Here is a nice explanation of the difference between sudo and gksudo:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by kamlapati on 2007-01-16
Sudo I already figured out. Thanks for the gksudo tip.

I notice that some programs request a password when executed from the graphical interface menu... how do the programs know to request a password? Is there a way to specify this in a menu config file somewhere?

---

### Post by ardchoille42 on 2007-01-16
> **kamlapati said:**
> Sudo I already figured out. Thanks for the gksudo tip.

I notice that some programs request a password when executed from the graphical interface menu... how do the programs know to request a password? Is there a way to specify this in a menu config file somewhere?

If you open some of the admin menu items, in /usr/share/applications, in gedit, you'll notice:

Exec=gksu users-admin

That was using /usr/share/applications/users.desktop as an example. The "gksu" part tells the system to require the admin password. I am thinking that some admin apps have the root requirement hard-coded in and some just won't allow you to use the app unless it has been run as administrator.. but that's just a guess.

---

### Post by kamlapati on 2007-01-17
Fantastic! Got it working.

Thanks for the quick and useful reply.

Kind regards,
Kamlapati

---

