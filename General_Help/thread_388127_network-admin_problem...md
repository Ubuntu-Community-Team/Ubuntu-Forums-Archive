---
title: "network-admin problem.."
date: 2007-03-19
forum: General Help
---

### Post by meditolafuga on 2007-03-19
Hi !

I have this problem..


1) At booting in /etc/resolv.conf file there is a wrong DNS that every-time I need to correct whit gedit and

2) every change that I made in network-admin will be lost ..
For sample I can enable my wireless


I am on edgy !

Thanks for help!

---

### Post by meditolafuga on 2007-03-19
Ok , I solved the problem about wireless setting the essid, magically work !

Now.. why the resolv.conf auto-rewrite ?

---

### Post by zvacet on 2007-03-19
After you are done with your modem>properties>select type of connection>close
you need to go to DNS and there is one address which isn´t your(I belive it is default)so delete it and put your nameservers>close
```
pppoeconf
```

---

