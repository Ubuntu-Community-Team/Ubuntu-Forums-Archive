---
title: "ssh login slow - delay at inetd sockets after dupping"
date: 2015-02-22
forum: General Help
---

### Post by Paul_Davison on 2015-02-22
Hi, I've looked all over but it's impossible to search on my problem because everyone's sshd debug log seems to contain the line at which my ssh logins are delayed but is not usually the actual rate limiting step.

I used an sshd command set to debug level 3.

My verbose sshd log is at the following pastebin link:

[http://pastebin.com/KmvByGCm](http://pastebin.com/KmvByGCm)

It hangs for about 10 seconds at line 123: inetd sockets after dupping

Everything else just zips through super fast.

The server runs Ubuntu 12.04.5 LTS
Output from uname -a
Linux linux 3.2.0-76-generic-pae #111-Ubuntu SMP Tue Jan 13 22:34:29 UTC 2015 i686 i686 i386 GNU/Linux

Has anyone seen this before or can anyone give any suggestions how to speed up the delay here? If you need any other configuration files / logs please let me know.

Ta

---

### Post by TheFu on 2015-02-22
Setup for encrypted connections is expensive. If the client and server don't immediately agree on the encryption to be used. There are ways to avoid the setup as much as possible: 
[http://linuxaria.com/howto/permanent-ssh-tunnels-with-autossh](http://linuxaria.com/howto/permanent-ssh-tunnels-with-autossh)
Reuse existing connections: [http://www.revsys.com/writings/quicktips/ssh-faster-connections.html](http://www.revsys.com/writings/quicktips/ssh-faster-connections.html)

Whatever you do, be certain to measure every change, so you know when a change really helps or not.
```
$ time ssh lubuntu ls /tmp

real    0m0.234s
user    0m0.052s
sys     0m0.004s
```

Rerunning the same command was a tiny bit faster:
```
real    0m0.232s
user    0m0.052s
sys     0m0.000s
```

Both of these machines have /etc/hosts entries for each other, so DNS doesn't slow things down.

---

