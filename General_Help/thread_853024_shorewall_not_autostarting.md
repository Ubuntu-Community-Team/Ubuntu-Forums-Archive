---
title: "shorewall not autostarting"
date: 2008-07-08
forum: General Help
---

### Post by sonicb00m on 2008-07-08
I have experienced this problem with Ubuntu before but Shorewall does not start on boot with Ubuntu. 

Shorewall blocks everything until the service is officially started.

How do I make sure it auto starts?

---

### Post by john.nicholls on 2008-07-09
Edit /etc/default/shorewall and change startup=0 to startup=1

---

### Post by niqmk on 2008-07-09
maybe the location at /etc/shorewall/shorewall.conf

---

### Post by sonicb00m on 2008-07-09
Sorry neither of those help. Shorewall wouldn't even start manually if that configuration file wasn't set to 1.

I'm not sure what you mean exactly with the 2nd option but startup enabled is already specified.

---

### Post by john.nicholls on 2008-07-10
The second option means (I think) that in /etc/shorewall.conf you have STARTUP_ENABLED=Yes.

If you can start Shorewall manually what about either putting it in the autostarted applications or manually starting it and saving the session?

---

### Post by sonicb00m on 2008-07-11
Yes, that's what I mean, that flag is also set.

The problem is I don't know much about the autostart stuff and I'd really prefer that gnome has nothing to do with it.

I run shorewall on my debian servers which are GUI less and I have no trouble with shorewall starting.

In fact, I've only had trouble with shorewall autostarting since using the new version of Hardy. 

It must be kind of starting since all the ports are blocked. It's only until I do a manual restart that the rules file starts working properly.

---

### Post by sonicb00m on 2008-07-28
I found my problem now.

It seems that somewhere down the line new versions of Ubuntu's start up have interferred with shorewalls start up scripts and now dynamic dns address can't be processed at boot time, most likely because the IP addresses haven't become registered in the system yet. That explains why the firewall will start when you manually kick it off once the desktop is loaded.

I contacted the makers of shorewall but they just don't give a ****. They told me that using DNS address was at my own risk and have no solution to this problem.

---

### Post by zaenal on 2010-01-29
There is something interesting in shorewall start up script : "WAIT_FOR_IFUP=/usr/share/shorewall/wait4ifup".
It seems that shorewall has designed to work using "ifupdown" network tools. And by default Ubuntu use "NetworkManager" to manage its network interfaces.

So, I have deactivated my NetworkManager and modify /etc/network/interfaces :
```
auto eth0
iface eth0 inet dhcp

```

And it works... :D

---

### Post by zaenal on 2010-02-09
To make sure managed interface already up before shorewall execute its script :

```

auto eth0
iface eth0 inet dhcp
up /etc/init.d/shorewall start
down /etc/init.d/shorewall stop

```

It much better now...but I miss Network Manager

---

