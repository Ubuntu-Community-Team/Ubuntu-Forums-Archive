---
title: "F-Spot Broken"
date: 2008-02-13
forum: General Help
---

### Post by travist120 on 2008-02-13
Hey, I haven't been able to get fspot working for a while lately and so I started f-spot through terminal and I get this error

```

An unhandled exception was thrown: System.NullReferenceException: A null value was found where an object instance was required.

  at System.Runtime.Remoting.Proxies.RealProxy.PrivateInvoke (System.Runtime.Remoting.Proxies.RealProxy rp, IMessage msg, System.Exception& exc, System.Object[]& out_args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

System.Transactions (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
System.Configuration (2.0.0.0)
System.Xml (2.0.0.0)
gconf-sharp (2.16.0.0)
gdk-sharp (2.10.0.0)
gnome-vfs-sharp (2.16.0.0)
Mono.Addins (0.2.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System (2.0.0.0)
Mono.Posix (2.0.0.0)
atk-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
Mono.Addins.Setup (0.2.0.0)
glib-sharp (2.10.0.0)
gnome-sharp (2.16.0.0)
f-spot (0.4.0.0)
Mono.GetOptions (2.0.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.22-14-generic i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
lenny/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"


```

and terminal spits this out
```

Starting new FSpot server
Can't get a connection to the dbus. Trying again...


```
any Ideas as to what might be wrong?

---

### Post by hamid.nyc on 2008-04-25
I'm having the same issue regarding dbus...

---

