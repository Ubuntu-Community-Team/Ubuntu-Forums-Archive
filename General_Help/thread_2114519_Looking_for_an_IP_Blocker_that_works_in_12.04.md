---
title: "Looking for an IP Blocker that works in 12.04"
date: 2013-02-10
forum: General Help
---

### Post by sandino1 on 2013-02-10
Hi everyone,

I just installed Ubuntu 12.04 and I'm trying to find an IP blocker that works on it. I would like to simply import a PPA and install a program, I don't want to have to compile anything.

I know about Peerguardian, MoBlock and IPlist, but none of them seem to be up-to-date enough to work on 12.04?

@jre - pgl doesn't come up in the software center, even after i add the PPA?

---

### Post by TheFu on 2013-02-10
A few options:
* denyhosts
* fail2ban
* iptables

I use fail2ban to dynamically firewall failed ssh login attempts.
I block entire countries using iptables with the help of country blocklists (which are not perfect).

---

### Post by jre on 2013-02-17
> **sandino1 said:**
> I know about Peerguardian, MoBlock and IPlist, but none of them seem to be up-to-date enough to work on 12.04?

@jre - pgl doesn't come up in the software center, even after i add the PPA?

MoBlock is supersed by pgl.

But pgl should work.
Add this to your /etc/apt/sources.list:
```
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu precise main 
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu precise main
``` 

and then do a ```
apt-get update
``` (I guess you forgot that in the first run.)

The packages are
pgld
pglcmd
pglgui

---

### Post by caffeinatedev on 2013-04-21
@jre your solution worked for me, thanks!

---

