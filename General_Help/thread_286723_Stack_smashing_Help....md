---
title: "Stack smashing? Help..."
date: 2006-10-28
forum: General Help
---

### Post by Denta on 2006-10-28
My fresh install of Edgy works perfect except for problems with installing nvclock. The one in the repos is too old for my hardware and therefore  I have downloaded the latest and installed with;

```
./configure
sudo make
sudo make install
```

However, when trying to use any of it's features it quits with

***** stack smashing detected ***: nvclock terminated**

I understand that this is some kind of protection included at compiletime, but i really need this app to work. How do I install nvclock without stack smashing protection? I've found the flag _-fno-stack-protector_ on google but i don't know exactly how to use it.

---

### Post by Denta on 2006-10-30
Anyone?

---

### Post by Slammer64 on 2006-10-30
Try: export CFLAGS="-fno-stack-protector" 
./configure && make && make install

---

### Post by Denta on 2006-10-30
Didn't make any difference. :???:

---

### Post by wally83 on 2006-12-07
I have exactly same problem with my gf 7300 GT.

Is it really so nobody knows fix for this? Maybe someone has nvclock 0.8 beta 2 .deb for Edgy (or at least for Ubuntu)?

---

### Post by Paulus on 2006-12-07
Just built this deb, with checkinstall for edgy-- might not work for all but give it a try!

I have just got a 7300gt ddr3 , but i'm dismayed to see that fanspeed control isn't supported in beta2 of nvclock for *only* 7300's :(

---

### Post by wally83 on 2006-12-11
Thanks for your help, Paulus!

Unfortunately it didn't work for me, same "*** stack smashing detected ***" -message appears.

---

### Post by Paulus on 2006-12-23
hmm :confused:  must be something else then.

I ended up just using a fan controller for my 7300

---

### Post by gschoper on 2007-01-11
I have been dealing with the stack smashing issue for a while with nvclock. I finally was able to compile a version of nvclock 0.8b2 with the "-fno-stack-protector" cflag that works for me every time. I did this by running the configure script and then manually editing all of the Makefile's in the tree and adding "-fno-stack-protector" (without the quotes) to all of the CC= lines.

Attached is a checkinstall .deb (Sorry, I know checkinstall sucks, but I don't have the time or patience for creating true .debs) built on Intel under Edgy.

gschoper

---

### Post by Megatog615 on 2007-06-08
This *still* occurs in Feisty!

---

### Post by notjohn101 on 2007-06-09
> **gschoper said:**
> I have been dealing with the stack smashing issue for a while with nvclock. I finally was able to compile a version of nvclock 0.8b2 with the "-fno-stack-protector" cflag that works for me every time. I did this by running the configure script and then manually editing all of the Makefile's in the tree and adding "-fno-stack-protector" (without the quotes) to all of the CC= lines.

Attached is a checkinstall .deb (Sorry, I know checkinstall sucks, but I don't have the time or patience for creating true .debs) built on Intel under Edgy.

gschoper

thisd actually fixed it for me in feisty

thanks

---

### Post by PastorTaz on 2007-07-19
If this still is not working for  you try compiling it with gcc-3.3, that worked for me on a program I wrote.

---

