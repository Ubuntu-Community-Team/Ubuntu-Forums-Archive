---
title: "[SOLVED] help with small script"
date: 2007-07-16
forum: General Help
---

### Post by dave37 on 2007-07-16
How can I turn the following terminal command in to a script that executes every boot up:

dpkg --get-selections | grep -v deinstall > ubuntu-files

and get it to copy to [ftp://username:password/path](ftp://username:password/path) to storage directory/ubuntu-files

thank you

---

### Post by bodhi.zazen on 2007-07-16
put your commands in /etc/rc.local just above "exit 0"

---

