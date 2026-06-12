---
title: "Locked myself out of sudo?"
date: 2008-05-22
forum: General Help
---

### Post by cjh79 on 2008-05-22
Hey all,

I think I did something bad.  I have an idea of what might have happened but let me explain the symptoms of the problem first: I can no longer do anything with sudo -- it seems to just fail silently.  Simple example:

cjh@boffo:~$ sudo ls
[sudo] password for cjh:
cjh@boffo:~$ 

(home dir is not empty...) I am not new to Linux, but sudo is kind of new to me.  It was working earlier just fine.  

I was messing around trying to add my user to a group earlier, and my suspicion is that I've inadvertently removed myself from whatever group I need to be in to use sudo (is there such a group?).  Does this even make sense?  I don't have another user on this machine, and without sudo I can't do anything, which makes the problem difficult to debug.  I can't even view /var/log/auth.log or /etc/sudoers without sudo.  Is there any way at all to log in to root?  Any other ideas?

I was planning on blowing away my install and upgrading to 8.04 this weekend anyways, so this isn't a complete disaster.  However it bothers me that I can't fix it.  I'd love some ideas.

Thanks,
Chris

---

### Post by Iowan on 2008-05-22
Boot into **recovery**, edit **/etc/group** and add yourself to the **admin** group. Better instructions [here.]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by mali2297 on 2008-05-22
Boot in recovery mode (an option in the Grub menu). Then you should be able to get to a terminal as root. From there, add your ordinary user to the *admin* group with the command
```

usermod -aG admin cjh

```
Finally, type
```

reboot

```
and return to the normal session.

---

### Post by cjh79 on 2008-05-22
Beautiful, thanks guys.  Why I didn't think of booting into recovery mode, I don't know...  I'll blame it on being new to Ubuntu.  duh.  #-o

---

### Post by gimfred on 2008-05-26
hehe... I've come here because I've done the same thing mate.

---

### Post by chinaxmsink on 2008-05-26
Now I know.Thanks you very much.---------------------------------------------------------------->We are the creators of beautiful handmade [copper sinks](http://www.china-sinks.com).

---

