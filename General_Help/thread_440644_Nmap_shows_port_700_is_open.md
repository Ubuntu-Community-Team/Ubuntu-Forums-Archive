---
title: "Nmap shows port 700 is open"
date: 2007-05-11
forum: General Help
---

### Post by fearevilleet on 2007-05-11
Hello,

I ran nmap on my box and it showed port 700 is open as an unknown service:

```
nmap 127.0.0.1

Starting Nmap 4.20 ( http://insecure.org ) at 2007-05-11 20:20 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1688 closed ports
PORT     STATE SERVICE
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
700/tcp  open  unknown
2049/tcp open  nfs
3306/tcp open  mysql
6000/tcp open  X11

```

Anyone have an idea what this port is open for? I googled around but could not find anything that specifically uses port 700 (programs, exploits, things like that)  I just want to make sure I was not hacked.

---

### Post by kidders on 2007-05-12
Hi there,

You could probably identify that port based on what's bound to it, with something like **sudo netstat -nle --program | grep 700**. In any case, it's unlikely that a service listening on the loopback interface would be useful for any kind of exploit. Unless you have reason to be paranoid (eg you're running a large mission-critical system), what's bound to 127.0.0.1 is largely irrelevant.

I hope that helps. I expect it's an RPC socket or something similar.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

