---
title: "is there a bug in 12.04lts software updater?"
date: 2013-08-24
forum: General Help
---

### Post by bdubawoop on 2013-08-24
installed 12.04lts a few weeks ago & haven't done much with it.

today, when i booted up the desktop software updater in upper right corner said it was up to date but because I hadn't
 booted in a couple weeks I ran it anyway.

it said 'not all updates can be installed' & offered a partial update or close.

when I told it to do partial update it errored out saying apt-get or aptitude was running, which it wasn't as far as I know.

I then did apt-get update from a terminal. it d/l a bunch & then exited normally. when i looked at the desktop updater
 it now said updates ready. 

It installed about 100 & exited normally.

I got a ton of hits on this with google but its not clear what the cause is.

is there some kind of conflict with the desktop updater if you run apt-get from a terminal or is there a bug
 in the desktop updater or what?

---

### Post by ibjsb4 on 2013-08-25
> **bdubawoop said:**
> is there a bug
 in the desktop updater or what?

Have a look here

[https://launchpad.net/ubuntu/+source/update-manager/+bugs](https://launchpad.net/ubuntu/+source/update-manager/+bugs)

---

### Post by bdubawoop on 2013-08-25
yikes, its not a bug, its bugS.

still confusing tho, particularly as it seemed to run normally after doing apt-get update.

i'll try it on my other computer which is set up similarly.

---

### Post by ibjsb4 on 2013-08-25
> **bdubawoop said:**
> still confusing tho, particularly as it seemed to run normally after doing apt-get update.

Yes, at times all it needs is a kick start :)

---

