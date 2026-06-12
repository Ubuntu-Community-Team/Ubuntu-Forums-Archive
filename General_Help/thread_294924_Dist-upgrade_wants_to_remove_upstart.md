---
title: "Dist-upgrade wants to remove upstart"
date: 2006-11-07
forum: General Help
---

### Post by ehamberg on 2006-11-07
When I run apt-get dist-upgrade, it tries to remove startup and replace it with sysvinit:

The following packages will be REMOVED
  startup-tasks system-services upstart upstart-compat-sysv upstart-logd
The following NEW packages will be installed
  sysvinit
0 upgraded, 1 newly installed, 5 to remove and 0 not upgraded.

Why does it do this? I want to keep using upstart... :)

---

### Post by michux on 2006-11-07
> **ehamberg said:**
> When I run apt-get dist-upgrade, it tries to remove startup and replace it with sysvinit:

The following packages will be REMOVED
  startup-tasks system-services upstart upstart-compat-sysv upstart-logd
The following NEW packages will be installed
  sysvinit
0 upgraded, 1 newly installed, 5 to remove and 0 not upgraded.

Why does it do this? I want to keep using upstart... :)

Why do you want to keep sysvinit? Upstart in Edgy is compatible with sysvinit but a bit faster :)
If you really want to keep sysvinit and have some good reasons to, you still can use /etc/apt/preferences to explicitly say so. Here is more on this subject: [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin)

---

### Post by Cable on 2006-11-07
I think he's saying he's simply checking for updates, and for some unknown reason **apt** wants to **remove** upstart and **replace** it with sysvinit.  He doesn't want this to happen, and is asking how to prevent it.

---

### Post by NoNo_231 on 2006-11-07
Do you have a dapper repository enabled? Or maybe a dapper cd at your sources.list? 

I had the same problem untill I commented the dapper cd at sources.list.

---

### Post by ehamberg on 2006-11-07
> **NoNo_231 said:**
> Do you have a dapper repository enabled? Or maybe a dapper cd at your sources.list? 

I had the same problem untill I commented the dapper cd at sources.list.

Ah, doh! Of course... :)

I used a dapper repository to install Linux 2.6.15 (2.6.17 has serious SATA problems, [https://launchpad.net/bugs/63937](https://launchpad.net/bugs/63937)).

I removed that repository, and now the problem is gone. Thanks! :)

---

