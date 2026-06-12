---
title: "How to add all users to a group"
date: 2007-02-06
forum: General Help
---

### Post by mkljun on 2007-02-06
Hi!

I have installed ubuntu (6.10) in a (computer) lab. Each workstation (36) 
authenticates users from LDAP. The problem I have is that none of these users 
can mount USB sticks, access audio devices, etc. 

What I would like to achieve is that every user would be automatically in these
groups (listed below). Is there a way to add them in? Like adding a star at the 
end of these lines:

cdrom: x :24:ubuntu
floppy: x :25:ubuntu
audio: x :29:ubuntu
dip: x :30:ubuntu
video: x :44:ubuntu
scanner: x :111:ubuntu
plugdev: x :46:ubuntu

I could grab all users from LDAP but I would have to do it every time a new
user would be added in a LDAP directory. 

Is there a way to add a group (instead of user) to a group?

thx

l pmk

---

### Post by mkljun on 2007-02-07
bump

---

