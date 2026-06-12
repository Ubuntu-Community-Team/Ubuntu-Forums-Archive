---
title: "Ubuntu newby having difficulties and needs HELP!!!"
date: 2007-10-29
forum: General Help
---

### Post by pkpmoa1536 on 2007-10-29
[SIZE="4"]I am having a little trouble with installing and downloading packages for Feisty.  I did not have any problems until just recently, now every time I try to open a package this error message pops up:



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



I am a novice with all this, and I'm not sure how to fix this with terminal or what to do.  PLEASE, any assisstance would greatly be appreciated.[/SIZE]

---

### Post by Crafty Kisses on 2007-10-29
> **pkpmoa1536 said:**
> [SIZE="4"]I am having a little trouble with installing and downloading packages for Feisty.  I did not have any problems until just recently, now every time I try to open a package this error message pops up:



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



I am a novice with all this, and I'm not sure how to fix this with terminal or what to do.  PLEASE, any assisstance would greatly be appreciated.[/SIZE]

Just run this command, and it should work:
```
sudo dpkg --configure -a
```

---

### Post by Maestro23 on 2007-10-29
> **pkpmoa1536 said:**
> [SIZE="4"]I am having a little trouble with installing and downloading packages for Feisty.  I did not have any problems until just recently, now every time I try to open a package this error message pops up:



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



I am a novice with all this, and I'm not sure how to fix this with terminal or what to do.  PLEASE, any assisstance would greatly be appreciated.[/SIZE]

First, try and do what it tells you. Open a terminal:

> sudo dpkg --configure -a

sudo apt-get update

sudo apt-get upgrade


---

### Post by pkpmoa1536 on 2007-10-29
That worked great.  Thanks for the help.

---

### Post by kemp_samurai on 2007-10-29
I'm also a relative newbie, and I just got my Wireless card to work, and now  have no acess to my administrative options whatsoever. And for this reason, I cannot change my hostname using the terminal or the standard networking interface. anyone have any ideas? :confused:

---

### Post by Buffalo Soldier on 2007-10-29
> **kemp_samurai said:**
> I'm also a relative newbie, and I just got my Wireless card to work, and now  have no acess to my administrative options whatsoever. And for this reason, I cannot change my hostname using the terminal or the standard networking interface. anyone have any ideas? :confused:

I think you will get more response (usually) by creating a new thread specifically about this problem.

---

### Post by Maestro23 on 2007-10-29
> **pkpmoa1536 said:**
> That worked great.  Thanks for the help.

No prob.  Don't forget to mark this SOLVED using the Thread Tools.

Thanks.:)

---

### Post by kemp_samurai on 2007-10-29
> **Buffalo Soldier said:**
> I think you will get more response (usually) by creating a new thread specifically about this problem.

right. sorry.

---

