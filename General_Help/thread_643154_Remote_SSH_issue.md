---
title: "Remote SSH issue"
date: 2007-12-17
forum: General Help
---

### Post by bcamp929 on 2007-12-17
Hello,

I am attempting to remotely connect to my Ubuntu Server 7.10 and am unable to do so.  This started with the upgrade to 7.10, never had this problem with 7.9.

I am able to ssh from my Mac to the Ubuntu box (within the network), but not outside the network.  I have checked the obvious router settings.  Port 22 is forwarded to the correct IP. 

Are there any suggestions?  I feel like I am missing something obvious. But can't come up with any answers.

Thanks!!!!

---

### Post by purdticker on 2007-12-17
[https://help.ubuntu.com/community/SSHHowto#head-7061606e8b2ed104c04d26f741cfe45b8b55d563](https://help.ubuntu.com/community/SSHHowto#head-7061606e8b2ed104c04d26f741cfe45b8b55d563)

You have the **openssh-server** package installed?

---

### Post by bcamp929 on 2007-12-17
Yes.  Sorry, that was an obvious to me. It installs with Server 7.10.

 Openssh-server and openssh-client are installed.

---

### Post by HermanAB on 2007-12-17
Check if sshd is running with 'ps -e' and telnet:
$ telnet localhost 22
You should get the SSH banner.

Cheers,

Herman

---

### Post by bcamp929 on 2007-12-17
Like i said in my first post, sshd is running, or I wouldn't be able to connect internally.  

The problem is connecting remotely.  openssh is installed and running, router is configured correctly, dyndns is setup properly.

---

### Post by bodhi.zazen on 2007-12-17
Look at the output of :

```
ssh -vv user@ip
```

---

### Post by Lostincyberspace on 2007-12-17
Is your isp throttling your ports maybe? Can you login any where else via ssh?

---

### Post by Keith Hedger on 2007-12-17
from the mac have you got remote login selected in the sharing panel?
i somtimes find that the firewall on my mac clashes with the one on my linux box try switching one or both off to narrow the problem

---

