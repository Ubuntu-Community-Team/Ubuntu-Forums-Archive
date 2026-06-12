---
title: "LAMP removal messed up ubuntu budgie DE"
date: 2021-08-12
forum: General Help
---

### Post by spectatorx on 2021-08-12
I have a really odd issue. Recently i needed to reinstall my lamp server on ubuntu budgie 20.04 but for some reason lamp removal also removed DE related packages for some reason. I will just present you logs from terminal and maybe you will be able to figure out what has happened and which package "nuked" my DE.


Here is lamp removal:
[https://pastebin.com/un7s6bEu](https://pastebin.com/un7s6bEu)

At this moment i haven't noticed yet that my budgie packages got removed together with lamp. Next step, as i wanted to reinstall lamp, i tried to install it back:
[https://pastebin.com/tAszpSyu](https://pastebin.com/tAszpSyu)

And now turns out i have one more issue: i'm unable to remove lamp because of packages conflict:
[https://pastebin.com/ZRkFgqWy](https://pastebin.com/ZRkFgqWy)

So now i have two problems:
1. "nuked" budgie DE
2. packages conflict causing problems with lamp reinstall.


I assume the easiest and laziest way to get rid off it would be to reinstall OS but that's not how linux is supposed to work in general. I understand many of you may want to suggest using docker, vagrant or any other virtual machine solution but please do not as that would be just temporary solution instead of proper permanent fix. I will be very thankful for help from you.

---

### Post by TheFu on 2021-08-12
**sudo apt install budgie-desktop budgie-desktop-environment**

I'm confused why those would be removed using the commands you used. But I don't install LAMP on a desktop.  I install each part of nginx, MariaDB, and Perl manually. Actually, I use perlbrew, not the system perl for my stuff so I can have 5 versions of perl installed concurrently and use the exact version and perl modules for each client project.

---

