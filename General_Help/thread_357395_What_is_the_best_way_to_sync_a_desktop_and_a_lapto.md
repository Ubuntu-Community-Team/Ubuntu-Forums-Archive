---
title: "What is the best way to sync a desktop and a laptop"
date: 2007-02-09
forum: General Help
---

### Post by Haegin on 2007-02-09
I have a desktop which I do all my work on at home, a server (which is always on and can boot the desktop and uses no-ip to give access from the world) and a laptop which I use at work and occasionally at home and around other places.

I would like the laptop to be able to connect to my main desktop but that isn't always on so I can't just use sshfs and mount the filesystems from wherever I go and that wouldn't work if I didn't have internet access either.

I am basically looking for a way to be able to work on both pcs and always be editing the current version and have it synced whenever I connect to the home network and both PCs are on. Does anybody know a way I could do this automatically? If so it would be great. I am looking into rsync and comparing modified times but I don't know how to get it all working together yet and any input from people already doing similar or trying to accomplish the same goal would be great.

---

### Post by SyvanX on 2007-02-09
I'm using 'unison' to sync up three computers.  Unison would need to be installed on both computers, and it handles the synchronization.  I have it setup to run at significant times using cron, before I go to school, before I get home, stuff like that. 

Basically it runs through ssh and uses a system like rsync, but does the comparisons for you.  You just give it two "roots" and it syncs them up.  There are options for batch mode (so it runs automagically) and a prefer option in case unison detects changes on both ends.

You can check it out here
[http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html](http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html)

Passwordless logins are a must, there are lots of tutorials for that, you can use ssh-agent or just a passwordless key (not recommended)

---

