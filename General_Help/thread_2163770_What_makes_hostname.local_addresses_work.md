---
title: "What makes hostname.local addresses work"
date: 2013-07-19
forum: General Help
---

### Post by hwttdz on 2013-07-19
I can connect from one of my machines to another using the hostname.local pattern, however I can't go the other direction.  

```
avahi-browse -tl _workstation._tcp --resolve
```

shows the machine I want to connect to, as well as a hostname.local name, and an ip.  The ip works, the hostname.local does not. ssh fails with a could not resolve hostname.

From the other machine both the hostname.local and the ip patterns work.

---

### Post by Morbius1 on 2013-07-19
*.local comes from Avahi on a Linux system and Bonjour on an Apple system. So for it to work on Linux it needs to be running:
```
sudo service avahi-daemon status
```
And port 5353 needs to be open.

Windows doesn't use avahi ( aka mDNS or Zerconf ) because it takes pleasure in the contortions that Linux users have in using Samba without it. You can however install it on WIndows by installing the following package from Apple: [http://support.apple.com/kb/DL999](http://support.apple.com/kb/DL999)

It's meant to allow Windows to find Bonjour printers but it installs a new service ( mDNSResonder.exe ) to windows so it should respond to a hostname.local query.

---

### Post by hwttdz on 2013-07-19
Thanks for the reply.  I'm still confused though.

Both machines are running linux and report that avahi is running.

---

### Post by Morbius1 on 2013-07-19
Other than a firewall getting in the way I don't have an answer at the moment. Try disabling the firewalls on both machines long enough to see if you can connect.

---

