---
title: "init?"
date: 2006-12-24
forum: General Help
---

### Post by lostguru on 2006-12-24
ok so after one of my coworkers ragged on me for long enough, i decided to try ubuntu at home instead of rhel.  ubuntu as a desktop machine is much nicer though i must admit i prefer rhel for my servers.  im still getting the hang of it and i have two burning questions:

1) why the h*** don't i get to set the root passwd when i install

2) i know that ubuntu doesn't have init so whats the equivelent of init 2, init 3, init 5?

prolly more to come but these popped up first

---

### Post by xopher on 2006-12-24
1) Because Ubuntu doesn't have a root account by default, 'use sudo' [tm] is applied instead.

2) Ok, I have no idea, if you care to elaborate what these are, and what you do with them I might learn something new ;)

3) Merry Christmas! (And a Happy New Year)

---

### Post by studiesrule on 2006-12-24
1) Security reasons. Ubuntu doesn't want you to screw up your sys by mistake. You can always set it later > sudo passwd
2) I'm not 100% sure what you want, but if its startup scripts, there are /etc/rcX.d where X is the runlevel. You can use the Preferences>Sessions tab to mod these too. For user scripts, use the rc.local file also in /etc.
3) Yup, merry Xmas to you all

---

### Post by gonesolo on 2006-12-24
> **lostguru said:**
> ok so after one of my coworkers ragged on me for long enough, i decided to try ubuntu at home instead of rhel.  ubuntu as a desktop machine is much nicer though i must admit i prefer rhel for my servers.  im still getting the hang of it and i have two burning questions:

1) why the h*** don't i get to set the root passwd when i install

2) i know that ubuntu doesn't have init so whats the equivelent of init 2, init 3, init 5?

prolly more to come but these popped up first


1:) Security, Ubuntu sets the password itself. As mentioned you can change it yourself later. but by default any actions requiring root permissions you should used the sudo command.

2:) Actually the init commands do function in ubuntu but they are root only so you'll have to preceed them with sudo.

---

### Post by pandu.rs on 2006-12-24
1. Where is the root account in ubuntu?
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

2. If you are using edgy it uses upstart (instead of init), but i use dapper. so i dont how to use upstart to get to a particular runlevel. but the following link might help you.

[http://upstart.ubuntu.com/doc/getting-started.html](http://upstart.ubuntu.com/doc/getting-started.html)

---

