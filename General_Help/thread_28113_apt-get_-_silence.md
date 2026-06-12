---
title: "apt-get - silence"
date: 2005-04-18
forum: General Help
---

### Post by NorLan on 2005-04-18
hi - could be that i missed something the last few days but
if i type apt-get update it loads
 
 Reading package lists... Done 

but since a week or one a half upgrade says 

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

what options do i have to test if my apt is broken or did i missed some messages in past (new repositories or else) ?

PS: i have used hoary before it becomes the new "stable" of ubuntu and the problems occure since this time (hoary release) -- or are there no sec updates since then -- i won't belive it

---

### Post by panzer77 on 2005-04-18
I don't think there has been much in the way of updates.  I loaded ubuntu about a week ago and have had nothing to update.

to check apt,  you could change the source by editing the source list...

sudo gedit /etc/apt/source.lists

Then uncomment these two lines to add universe (source)..(uncomment = remove the leading # symbol).

deb _[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)_ hoary universe multiverse
deb-src _[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)_ hoary universe multiverse

FYI - Remember anthing from the universe repositories are entirely unsupported by ubuntu. :-?

---

### Post by NorLan on 2005-04-19
my sources.list is:

```
## ubuntu
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted
``` 

but should be ok if there are no updates during last 2 weeks - it is strange but ok *gg

---

