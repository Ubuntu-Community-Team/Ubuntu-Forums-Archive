---
title: "Mounting OS X partition in Ubuntu"
date: 2006-07-22
forum: General Help
---

### Post by eyebrowman92 on 2006-07-22
I've recently installed Ubuntu Dapper on my Black MacBook, 2.0GHz Dual-Core processors, 1gig of ram, and an 80Gig HD.To boot, I'm using rEFIt, which is so far working fine. It has it's own systen partition which is ~220mb. This partition is sda1.My OS X partition takes up ~65gigs, and is sda2. Finally, my Ubuntu partition takes up around 11gigs, and is sda3. I've installed the tools that come up when you search "hfs" in Synaptic, but 
```
sudo mount -t hfs+ /dev/sda2 /osx
```
doesn't work. I get an unknown File-System error. There has to be more tools to install to get it mounted. What are those tools, and if it isn't the tools, how do i get this to work?

---

### Post by aysiu on 2006-07-22
Maybe it's ```
sudo mount -t hfsplus /dev/sda2 /osx
```

---

### Post by eyebrowman92 on 2006-07-22
Haha that worked. Thanks.

---

