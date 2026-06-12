---
title: "Firstclass client 8.013"
date: 2006-08-04
forum: General Help
---

### Post by Kakistos on 2006-08-04
I've installed the above version of firstclass on dapper.  I got it as an rpg file and aliened it to a deb.  The trouble is firstclass wont start up.  
If I go to the link in Apps-internet firstclass flashes up on the task bar for several seconds and just disappears.  If I type fcc into the terminal I get the following:-

chris@ubuntu:~$ fcc
*** glibc detected *** free(): invalid pointer: 0x085fb6d0 ***
Aborted

Any ideas.

Thanks

Chris

---

### Post by trivialpackets on 2006-08-06
try this from terminal

cd /opt/firstclass

./fcc

it should tell you what is missing.
libqt-mt and something else I think.  Give it a shot.  Then just apt-get them or synaptic and it should be fine.

---

### Post by Kakistos on 2006-08-06
Tried that and this is the output.

chris@ubuntu:~$ cd /opt/firstclass
chris@ubuntu:/opt/firstclass$ ./fcc
*** glibc detected *** free(): invalid pointer: 0x085fb6d0 ***
Aborted
chris@ubuntu:/opt/firstclass$

Thanks

C

---

### Post by trivialpackets on 2006-08-06
Try a different build perhaps?  I am using one of the builds from the how to on first class.  Do a search for firstclass and it comes up.  Here's the link to the one I'm using.

 [http://reflex.at/files/fcc-8.090-1-Linux-i686.deb](http://reflex.at/files/fcc-8.090-1-Linux-i686.deb)

---

### Post by Kakistos on 2006-08-07
Cheers for the link, all sorted now.  The problem must have been the version I was using.

Chris

---

