---
title: "Symbolic Link question"
date: 2007-09-11
forum: General Help
---

### Post by PreviousN on 2007-09-11
Hey everyone, I don't usually have questions, but this one has been bugging me for a while. I want to use Symbolic links to merge two directories on different file systems into one big directory. 

== More info ==
/media/hdb1/ShareHome has Dir1 and Dir2 in it. Dir1 is an fstab mounted samba share with 50 or so different subdirectories and Dir2 is a local  filesystem with a similar number of subdirectories. I want to make an "all" folder with symlinks to all 100 subdirectories from Dir1 and Dir2 so everything is in one place.

I know ln -s can make a directory symbolically linked:

so i put in a terminal:
ln -s /media/hdb1/ShareHome/Dir1 /media/All
ln -s /media/hdb1/ShareHome/Dir2 /media/All

which results in All containing only Dir1 and Dir2, not only the sub folders of which.
cd /media/All
ls = Dir1     Dir2

I want it to show subdirectories of Dir1 and Dir2...basically I want to link to the sub directories. Do I have to do this one by one like this?

ln -s /media/hdb1/ShareHome/Dir1/SubDir1 /media/All
...
ln -s /media/hdb1/ShareHome/Dir1/SubDir100 /media/All

This would be ok if I only had 10 or so subdirectories, but I've got like 100. Is there a quick/automated way to do this?

Thanks -

---

### Post by jocko on 2007-09-11
Try this:
```
ln -s /media/hdb1/ShareHome/Dir1/* /media/All
ln -s /media/hdb1/ShareHome/Dir2/* /media/All
```

---

### Post by rivalarrival on 2007-09-11
Setup a bash script to grab all the directory names and issue the command for each one.

---

### Post by PreviousN on 2007-09-11
Thanks rivalarrival, before that I think I'll try jocko's idea though (sounds easier).

---

### Post by rivalarrival on 2007-09-11
Yeah, probably...  I'm doing a lot of things with shell scripting lately. When you work with a hammer all day, everything looks like a nail... :)

---

