---
title: "/etc/inittab missing??"
date: 2007-11-22
forum: General Help
---

### Post by jaspreet on 2007-11-22
I have ubuntu 7.10 installed. I do not se /etc/inittab on my system. Any ideas?

---

### Post by dkulchenko on 2007-11-22
I just switched from Fedora to Ubuntu and noticed the same thing. After some searching, it appears to me that /etc/inittab does not exist on Ubuntu. It has been replaced by  /etc/event.d/* . In that folder, there are files for each runlevel and a general file called 'rc-default', the equivalent of inittab. 

So, if you want to edit that, the new "inittab" file lives at /etc/event.d/rc-default

---

### Post by jaspreet on 2007-11-22
Good to know that. Thank you so much. 

Have you tried to add some commands to rc.local on ubunut? did it work for you?

---

### Post by juan@forum on 2007-11-22
there is a service rc.local, you need to activate that service on boot in order to execute /etc/rc.local

---

### Post by dkulchenko on 2007-11-22
yep, he's right. that's what i did and it worked for me.

by the way, if you need to migrate from an old inittab the the event.d, there's a script at /usr/lib/upstart called migrate-inittab.pl which converts an old one to a new one.

Glad I could help! :)

---

### Post by barrycom on 2007-11-25
I was in need of being able to have distinct different run levels and be able to set the run level that I wanted to have executed.  So... here is what I did.

 I deleted the files from /etc/rc3.d , /etc/rc4.d and rc5.d that I did not need / want running at that run level... 

Such as I deleted /etc/rd3.d/S30gdm since I did not want a GUI in run level 3 (command line boot).

I created a standard /etc/inittab file and everything functions as it would had this upstart thing not come to be.

Just an fyi

Cheers

---

