---
title: "unison problem: version mismatch (but not really)"
date: 2005-09-01
forum: General Help
---

### Post by jpkotta on 2005-09-01
I've used unison for a while to sync my USB key drive.  I recently got a laptop and I want to use it for that too.  I'm trying to use an ssh connection.  ssh works fine; I can remote login and scp from laptop to desktop and vice versa.  The -socket option works, but I'd much rather use ssh.  unison always dies with an error similar to: 
> [jpkotta@goedel ~]$ unison -testServer foo/ ssh://192.168.0.7/home/jpkotta/foo 
Contacting server... 
Password:  
Fatal error: Received unexpected header from the server:  expected "U" but received "W". This is probably because you have different versions of Unison installed on the client and server machines.  
The "expected" letter is always "U", "received" letter changes everytime.  I read somewhere else that this error should probably be some thing more like 
> Expected "Unison v.v.v" but received "Unison v'.v'.v'" 
where the v's are the version.  I've tried rsh connection too.  I've tried removing unison completely and `rm -rf ~/.unison unison.log` on both machines. I'm using Hoary, so it's unison version 2.9.1.

---

### Post by jpkotta on 2005-09-03
I found the problem.  I run fortune from ~/.bashrc, and ssh kept seeing fortunes instead of the server's header.  Moving fortune to ~/.bash_profile fixed the problem.

---

