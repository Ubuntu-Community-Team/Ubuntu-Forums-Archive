---
title: "howto allow to see windows XP directories as a normal user ?"
date: 2007-03-05
forum: General Help
---

### Post by cccc on 2007-03-05
hi

I have dapper drake and windows xp installed on the same computer.
windows xp is mounted in /etc/fstab:```

/dev/hda1       /windows        ntfs    ro,auto,user    0       0

``` but I cannot see windows directories as a normal user.
howto allow normal user to see windows files ?

---

### Post by annda on 2007-03-05
what about following aysiu's guide ([http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)) and modifying the fstab line to:

/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0

this should help. (the umask option is important, because it sets r+x permissions)

by the way, you can add 'defaults' before nls......

---

### Post by cccc on 2007-03-06
thanks, 

now it works.

---

