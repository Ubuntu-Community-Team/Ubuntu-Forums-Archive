---
title: "problem in netbeans installation"
date: 2008-02-16
forum: General Help
---

### Post by egyptioneagle on 2008-02-16
i have problem when i install netbeans .sh file 
it give me this error "[SIZE="5"]No X11 DISPLAY variable was set, but this program performed an operation which requires it[/SIZE]"
i installed jdk6
pleas i want to know the problem and how can i solve it

---

### Post by Shippou on 2008-02-16
To be honest, I do not know how to install netbeans... But then in my opinion (and also the opinion of my other CS classmates) netbeans is for beginners.

I would like to suggest you abort installing netbeans and install notepad++ instead. It is an open source software and you can download the .exe file at [www.download.com](www.download.com) (just install wine and run the installer), or at any other site.

Or if you like, just install eclipse.

Nice day... :)

---

### Post by seventhc on 2008-02-16
How did you install it, and what version?
I would try the version in synaptic, I just installed it and it opens fine.
It is 5.5 so not the 6.0.1 version but it does work.

---

### Post by oregonbob on 2008-04-25
I had same experience installing netbeans 6.0.1.
How did I install? As per instructions, download a giant sh archive and execute it. It clicks through numerous steps OK, but dies when it trie to open a window with "No X11 DISPLAY variable was set, but this program performed an operation which..." error.

Stuck!

---

### Post by urlwolf on 2008-04-26
I installed the version in synaptic.
It doesn't boot, it gets stuck on 'done loading modules'. It shows a large x window, all grey.

I moved from 7.10 to 8.04 and it completely borked netbeans. I had a working installation before, so I'm going back just because I need this to work day to day. 

PS: netbeans in my personal experience does get stuck a lot for random reasons.

---

### Post by Linja on 2008-04-26
The DISPLAY error may be caused by running the installer with root privileges. I always install netbeans to a "netbeans" folder under /opt. After creating that folder, I do chown -R username.username /opt/netbeans so that it is effectively owned by me. I can then run the installer as a regular user.

---

### Post by ibutho on 2008-04-26
Try installing netbeans by doing the following
```
xhost +localhost
sudo sh netbeans-<VERSION>.sh

```
Install it to /opt because thats where packages like netbeans belong (if being installed globally).

---

### Post by rajathshanbag on 2008-05-14
why not use 
   
   xhost +localhost 
   gksudo sh netbeans-installation.sh

in non root user mode!:guitar:

---

### Post by dcbc on 2008-05-16
i followed the instructions here.
i am a linux newbie.i had no problem installing netbeans 6.
i hope this helps.
[http://wiki.netbeans.org/InstallingNetbeans6.0OnUbuntu7.10](http://wiki.netbeans.org/InstallingNetbeans6.0OnUbuntu7.10)

---

