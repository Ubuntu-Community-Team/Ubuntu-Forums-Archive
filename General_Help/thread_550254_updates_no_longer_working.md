---
title: "updates no longer working"
date: 2007-09-13
forum: General Help
---

### Post by s0c9 on 2007-09-13
I am having problems getting updates to work on Edgy
searched forum - tried everything I can find, including clean , etc.
my sources.list  is OK. tried the fpt/http switch..nada
I can reach the target in firefox OK.
Firefox and internet connection works fine.
I am behind a firewall,  and package manager has the correct proxies
When I run update, I get this.


```
root@ubuntu:/etc/apt# apt-get update
Err http://us.archive.ubuntu.com edgy-updates Release.gpg                                      
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err ftp://security.ubuntu.com edgy-security Release.gpg                                        
  Could not connect to security.ubuntu.com:21 (82.211.81.138), connection timed out
Err http://us.archive.ubuntu.com edgy-updates/main Translation-en_US                           
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.6), connection timed out
Err ftp://security.ubuntu.com edgy-security/main Translation-en_US                             
  Could not connect to security.ubuntu.com:21 (82.211.81.138), connection timed out
0% [Connecting to us.archive.ubuntu.com (91.189.89.6)] [Connecting to security.ubuntu.com (91.1

```

Any suggestions would be apprecaited
Sock

---

