---
title: "scp has warning every time - can't transfer files"
date: 2007-12-22
forum: General Help
---

### Post by SnakeByte29 on 2007-12-22
Every time I attempt to run scp (after having ssh'ed to my other PC) to copy a file from my Windows PC (running Cygwin for an ssh server) I get a warning: "Remote host identification has changed." Because of this, I can't transfer files as I could when I was running Feisty (I am using Gutsy now). Does anyone know what may be causing this problem?

---

### Post by chippy99 on 2007-12-22
Something has changed on the remote host since you last logged into it (ip address or hostname). If you delete the file ~/.ssh/known_hosts it should work again. First time you connect you will be asked if want to connect to this machine and it will recreate the entry in known hosts file.
This is a security feature to sop people spoofing machines so be sure that you sre connecting to the correct machine.

---

