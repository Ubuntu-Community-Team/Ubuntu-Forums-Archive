---
title: "Wargus installation problem"
date: 2007-12-20
forum: General Help
---

### Post by Grout58 on 2007-12-20
Im having some problems installing wargus under gutsy. So I installed stratagus from the repo and downloaded wargus from the site. The readme says run ./build.sh -p /media/cdrom0 Thats where my wacraft 2 cd is. When I run it I get permission denied so I use sudo ./build.sh -p /media/cdrom0 and that gives me sudo: ./build.sh: command not found. So then I used sh build.sh -p /media/cdrom0 and that gives me
grout@ubuntu:~/Desktop/wargus-2.2.4$ sudo sh build.sh -p /media/cdrom0/ /home/grout/wargus
: not found7:
: not found1:
: not found4:
: not found7:
: not found0:
: not found3:
: not found5:
build.sh: 47: Syntax error: word unexpected (expecting "in")
So now im really not sure what to do.. Anyone got any ideas?

---

### Post by zivagolee on 2008-02-21
stupid authors used windows.

do this:

dos2unix build.sh

then run it again (you will need the unix2dos package if its not installed yet)

---

