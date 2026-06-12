---
title: "What is Lubuntu's network manager?"
date: 2012-12-10
forum: General Help
---

### Post by agxryt on 2012-12-10
I've been reading some stuff on using wicd as opposed to nm, in relation to a problem another forum user had posted.

It's suggestion was the removal of the network-manager package, and installation of the wicd package.

WELL. I can't find any network-manager package in my system to remove or even tinker with :/ All I could find was nm-applet. 

tl;dr how do I start/remove the standard lubuntu network manager?

I've installed wicd, and invoking it in terminal just gives "daemon is already started"

I'm really just looking for some explanation as to what is going on :P

---

### Post by Dennis N on 2012-12-10
The default Lubuntu installation uses network-manager, same as Ubuntu.

---

### Post by agxryt on 2012-12-10
> **Dennis N said:**
> The default Lubuntu installation uses network-manager, same as Ubuntu.

Yeah, I found it.

network-manager-gnome.

It's just that when I invoke it in terminal, it says command not found. But I can uninstall it. Why is that?

---

### Post by Dennis N on 2012-12-10
> **agxryt said:**
> Yeah, I found it.

network-manager-gnome.



There IS a package named network-manager installed on your system:

```
dn@Alexa:~$ apt-cache policy network-manager
network-manager:
  Installed: 0.9.6.0-0ubuntu7
  Candidate: 0.9.6.0-0ubuntu7
  Version table:
 *** 0.9.6.0-0ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
```

Also see for more details:

[http://packages.ubuntu.com/quantal/network-manager](http://packages.ubuntu.com/quantal/network-manager)

---

### Post by agxryt on 2012-12-10
> **Dennis N said:**
> There IS a package named network-manager installed on your system:

```
dn@Alexa:~$ apt-cache policy network-manager
network-manager:
  Installed: 0.9.6.0-0ubuntu7
  Candidate: 0.9.6.0-0ubuntu7
  Version table:
 *** 0.9.6.0-0ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
```Also see for more details:

[http://packages.ubuntu.com/quantal/network-manager](http://packages.ubuntu.com/quantal/network-manager)

Yeah!

```
ben@computer06:~$ apt-cache policy network-manager
network-manager:
  Installed: 0.9.4.0-0ubuntu4.1
  Candidate: 0.9.4.0-0ubuntu4.1
  Version table:
 *** 0.9.4.0-0ubuntu4.1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.9.4.0-0ubuntu3 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

But how come I can't just run these applications in the terminal? I thought you could basically do that with anything :S

---

### Post by Dennis N on 2012-12-10
> **agxryt said:**
> 
But how come I can't just run these applications in the terminal? I thought you could basically do that with anything :S

It (network-manager) has already started up during the boot process. That's why.

---

### Post by agxryt on 2012-12-10
> **Dennis N said:**
> It (network-manager) has already started up during the boot process. That's why.

I still don't really understand. Why wouldn't it give an "already running" exception, instead of just "doesn't exist lol"

Either way, I just learned about nmcli, so I should be good to go. Thanks a bunch!

---

