---
title: "Proftpd stopped working at port 21"
date: 2006-09-26
forum: General Help
---

### Post by Ravix on 2006-09-26
I've been running an ubuntu 6.06 server for a while now and I never had any real problems in setting it up and configuring it. 

But now I do have an annoying problem with proftpd. Although I'm not sure the problem is caused by proftpd itself or something else. 
It just popped up today: earlier this day everything went fine, users were able to connect to proftpd at port 21. But now I get an 'unable to connect' error when I try to login (like no program is listening on port 21). 
However, when I configure proftpd to listen on any other port (e.g. port 2121), everything does work correctly.
I've really no idea of what might be causing this problem, I've verified that no other process is listening on port 21 (with 'sudo netstat -anp').

Any thoughts?

---

### Post by wieman01 on 2006-09-27
_2 questions:_

1. Have you installed any kind of firewall in the meantime?
2. Does the same happen when you log on to your FTP server from the local host (i.e. the very same machine)?

---

### Post by Ravix on 2006-09-27
I must say, today everything works fine again. I don't quite understand how this problem suddenly disapeared.

To answer your questions:
1. no, I haven't installed a firewall on that machine
2. Yes that did work (I tried that yesterday as well)

But again: at this very moment I have no problems at all with logging in on port 21 from remote machines.

---

