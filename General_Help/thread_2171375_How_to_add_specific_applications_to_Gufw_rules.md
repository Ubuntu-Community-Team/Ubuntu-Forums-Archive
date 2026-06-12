---
title: "How to add specific applications to Gufw rules?"
date: 2013-08-30
forum: General Help
---

### Post by Abhishek_K._Pandey on 2013-08-30
Hello all.
I want to ask that how can one add rules for specific applications in Gufw to allow or deny or anything else.

Its like, I would like to have a default rule in ufw to deny incoming as well as outgoing.
Then, I'll specifically allow apps., to communicate via internet. These apps may include Firefox, Thunderbird, USC, synaptic etc.
I have seen gufw documentation, but it only tell about ports. If all we have to do is via ports only, then how can we know specific ports?

Further, if I want to give an app. temporary permission, then how that could be done. By temporary permission, I mean, I'll allow access, at app start and then such rules will end as soon as app closes. So, next time it'll again need permissions.

Regards.

---

### Post by GwL3eNC on 2013-08-30
Hello,

i believe there is no easy way in ufw/Gufw to make firewall rues for specific apps. The only way
you can try is iptables (--gid-owner groupid) where every allowed or denied app must be
a seperate group.

Port finding is not easy for me, there are some sides in the www listing them but can i trust them.
If i cant find information about a specific port i use some iptables logging. Therefore i deny everything 

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

and set the logging rues

iptables -A INPUT -j LOG --log-level debug --log-prefix "LOG_IN: " 
iptables -A OUTPUT -j LOG --log-level debug --log-prefix "LOG_OUT: " 
iptables -A FORWARD -j LOG --log-level debug --log-prefix "LOG_FOR: " 

Then i can view var/log/syslog to find out whats blocked. I do that with a

cat /var/log/sysog | grep LOG_OUT 

for example.

---

### Post by Abhishek_K._Pandey on 2013-09-01
So that means its not possible to add specific applications easily......
Some solution should be found, as it will give more control to user.

---

### Post by mcduck on 2013-09-01
You'll definitely have a hard time finding any Linux firewall that would do per-application filtering, as the generic idea is that you shouldn't install an application if you can't trust it.

However there are some solutions. More common ways to handle this kind of application-specific rules would be AppArmor or SE-Linux.

There is also a project that is working on creating such firewall, although I don't know how well it's working and it seems it hasn't been updated for over a year now: [http://sourceforge.net/projects/leopardflower/]("http://sourceforge.net/projects/leopardflower/")

---

### Post by 3rdalbum on 2013-09-01
> **Abhishek_K._Pandey said:**
> So that means its not possible to add specific applications easily......
Some solution should be found, as it will give more control to user.

I'd say that if this was a necessary security feature on Linux, developers would have already added it. The only ways an attacker can realistically get code onto a normal, non-server desktop Linux computer are by tricking the user into downloading malicious software/maliciously-crafted file, or by exploiting a security flaw in a network-facing piece of software like Firefox. The former is unheard of on Linux, and the latter will not be stopped by an application-specific outgoing firewall. Not to mention, when there's malicious code running on a desktop Linux system, there are a couple of ways it can eventually gain root and simply turn off the firewall. Game over, your application-specific firewall was completely useless.

"More control" sounds great, until you remember that computers are meant to make our lives easier and increase productivity, not to make our lives more stressful and cause us to waste time tending and maintaining them. I prefer to concentrate my attention toward my work and security systems that will really help.

---

### Post by Abhishek_K._Pandey on 2013-09-01
> **mcduck said:**
> You'll definitely have a hard time finding any Linux firewall that would do per-application filtering, as the generic idea is that you shouldn't install an application if you can't trust it.

However there are some solutions. More common ways to handle this kind of application-specific rules would be AppArmor or SE-Linux.

There is also a project that is working on creating such firewall, although I don't know how well it's working and it seems it hasn't been updated for over a year now: [http://sourceforge.net/projects/leopardflower/](http://sourceforge.net/projects/leopardflower/)

I agree that one should not install an application he don't trust. But stil there could be instances when I need an app to connect with, when I want and not otherwise.

I just checked and find that apparmor is already installed in system. I think its a default one.

---

### Post by steeldriver on 2013-09-01
I don't use Gufw, but the underlying ufw has an application profile mechanism, which lets you do things like

```
sudo ufw allow OpenSSH
```

```

$ sudo ufw app list
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH

```

The profiles are stored in /etc/ufw/applications.d

```

$ ls /etc/ufw/applications.d/
apache2.2-common  openssh-server

```

and there's really nothing to stop you writing your own, I'm sure there's a guide out there somewhere

```

$ cat /etc/ufw/applications.d/openssh-server
[OpenSSH]
title=Secure shell server, an rshd replacement
description=OpenSSH is a free implementation of the Secure Shell protocol.
ports=22/tcp

```

---

### Post by Abhishek_K._Pandey on 2013-09-01
> **3rdalbum said:**
> I'd say that if this was a necessary security feature on Linux, developers would have already added it. The only ways an attacker can realistically get code onto a normal, non-server desktop Linux computer are by tricking the user into downloading malicious software/maliciously-crafted file, or by exploiting a security flaw in a network-facing piece of software like Firefox. The former is unheard of on Linux, and the latter will not be stopped by an application-specific outgoing firewall. Not to mention, when there's malicious code running on a desktop Linux system, there are a couple of ways it can eventually gain root and simply turn off the firewall. Game over, your application-specific firewall was completely useless.

"More control" sounds great, until you remember that computers are meant to make our lives easier and increase productivity, not to make our lives more stressful and cause us to waste time tending and maintaining them. I prefer to concentrate my attention toward my work and security systems that will really help.

But if we think like that, doesn't it end any need of firewall at all!!!!!!!!

---

### Post by Abhishek_K._Pandey on 2013-09-01
> **steeldriver said:**
> I don't use Gufw, but the underlying ufw has an application profile mechanism, which lets you do things like

```
sudo ufw allow OpenSSH
```

It's just that few application developers seem to provide profiles for it

```

$ sudo ufw app list
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH

```

The profiles are stored in /etc/ufw/applications.d

```

$ ls /etc/ufw/applications.d/
apache2.2-common  openssh-server

```

and there's really nothing to stop you writing your own, I'm sure there's a guide out there somewhere

```

$ cat /etc/ufw/applications.d/openssh-server
[OpenSSH]
title=Secure shell server, an rshd replacement
description=OpenSSH is a free implementation of the Secure Shell protocol.
ports=22/tcp

```

Will see that in a while. I am not a techie guy :-)

---

### Post by mcduck on 2013-09-01
Well, it pretty much does. You should only need a firewall on very specific (and not so common) situations. For example when running a server application that would listen for incoming network connections, but for some reason lacks the necessary configuration options to protect itself.

Any normal setup, deskop or server, should be just fine without a firewall. All you need to do is make sure you only install applicatiosn you can trust, and if you install a server application, configure it properly for whatever use case you installed it for.

Anyway, AppArmor is part of the kernel so yes, it's installed. But it's not a firewall but a toolset that allows you to configure various rules for applications. So you'll need to give it some custom rules to work with: [https://wiki.ubuntu.com/AppArmor]("https://wiki.ubuntu.com/AppArmor") (And no, that's not very easy or simple, but as such configurations would definitely fall under "rare & advanced"use cases the tools do as well ;))

edit: Here's the 13.04 Server Guide's page on AppArmor: [https://help.ubuntu.com/13.04/serverguide/apparmor.html]("https://help.ubuntu.com/13.04/serverguide/apparmor.html")

---

### Post by Abhishek_K._Pandey on 2013-09-02
> **mcduck said:**
> Well, it pretty much does. You should only need a firewall on very specific (and not so common) situations. For example when running a server application that would listen for incoming network connections, but for some reason lacks the necessary configuration options to protect itself.

Any normal setup, deskop or server, should be just fine without a firewall. All you need to do is make sure you only install applicatiosn you can trust, and if you install a server application, configure it properly for whatever use case you installed it for.

Anyway, AppArmor is part of the kernel so yes, it's installed. But it's not a firewall but a toolset that allows you to configure various rules for applications. So you'll need to give it some custom rules to work with: [https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor) (And no, that's not very easy or simple, but as such configurations would definitely fall under "rare & advanced"use cases the tools do as well ;))

edit: Here's the 13.04 Server Guide's page on AppArmor: [https://help.ubuntu.com/13.04/serverguide/apparmor.html](https://help.ubuntu.com/13.04/serverguide/apparmor.html)
Thanks. Will go through and tell!!

---

### Post by Abhishek_K._Pandey on 2013-09-03
> **steeldriver said:**
> I don't use Gufw, but the underlying ufw has an application profile mechanism, which lets you do things like

```
sudo ufw allow OpenSSH
```

```

$ sudo ufw app list
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH

```

The profiles are stored in /etc/ufw/applications.d

```

$ ls /etc/ufw/applications.d/
apache2.2-common  openssh-server

```

and there's really nothing to stop you writing your own, I'm sure there's a guide out there somewhere

```

$ cat /etc/ufw/applications.d/openssh-server
[OpenSSH]
title=Secure shell server, an rshd replacement
description=OpenSSH is a free implementation of the Secure Shell protocol.
ports=22/tcp

```
Well, that seems easy if one know how to create profiles, which in turn needs one to know port info :-)
> **mcduck said:**
> Well, it pretty much does. You should only need a firewall on very specific (and not so common) situations. For example when running a server application that would listen for incoming network connections, but for some reason lacks the necessary configuration options to protect itself.

Any normal setup, deskop or server, should be just fine without a firewall. All you need to do is make sure you only install applicatiosn you can trust, and if you install a server application, configure it properly for whatever use case you installed it for.

Anyway, AppArmor is part of the kernel so yes, it's installed. But it's not a firewall but a toolset that allows you to configure various rules for applications. So you'll need to give it some custom rules to work with: [https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor) (And no, that's not very easy or simple, but as such configurations would definitely fall under "rare & advanced"use cases the tools do as well ;))

edit: Here's the 13.04 Server Guide's page on AppArmor: [https://help.ubuntu.com/13.04/serverguide/apparmor.html](https://help.ubuntu.com/13.04/serverguide/apparmor.html)
That seems a bit technical for me :-(

---

