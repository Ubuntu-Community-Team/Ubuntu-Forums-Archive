---
title: "Firestarter"
date: 2008-05-20
forum: General Help
---

### Post by Clayton South on 2008-05-20
Hello everyone,

Quick question: I'm running Firestarter in Ubuntu 8.04 and I have added it to the sessions at startup using gtksu firestarter. I'm not the administrator and every time I log in and start up, in order to start firestarter  I have to enter the admin password. How can I, using permissions, allow firestarter to start up with Ubuntu, all without needing to enter the password of the Admin?

Thanks!

-Clayton South

---

### Post by mardawi on 2008-05-21
I know that you should add it to the boot services not the session if it needs root permession. I'm not sure if this is the best way to add a new boot service, I've never done it before, but if I were you, and don't mind my system crash, I will use:```
sudo update-rc.d firestarter default
``` if things go bad, and your system doesn't boot again, you **might** be able to reverse it by booting using the safe mode option (or whatever the name is) in the grub menu which should give you a command terminal with root access to the system and write```
update-rc.d firestarter remove
```

Good luck, let me know if it works. If you don't want to risk it, then wait for more experienced users to comment.

---

### Post by Anduu on 2008-05-21
Just so you know Firestarter is merely a front-end for the built in Linux firewall.It is not necessary to have it run at startup.

---

### Post by Clayton South on 2008-05-21
> **Anduu said:**
> Just so you know Firestarter is merely a front-end for the built in Linux firewall.It is not necessary to have it run at startup.

Thanks for the reply. 

Right now, as you probably know, by typing ufw at the command-line you can set the options for the firewall. To get ufw to run every time at startup must I continue to go to the command line and type it in?

And, how is firestarter simply a front-end for the built-in linux firewall? I thought ubuntu didn't have a firewall built-in...which is why programs like firestarter were needed...

Thoughts?

-Clayton South

---

### Post by Clayton South on 2008-05-21
bump.

---

### Post by DMK62 on 2008-05-21
Not running 8.04 so can't answer the ufw question.

Firestarter and ufw are just front ends to iptables. Firestarter is not installed by default in Ubuntu. Iptables is basically packet filtering.

Dale

---

### Post by zvacet on 2008-05-22
> Iptables is a firewall, installed by default on all official Ubuntu distributions (Ubuntu, Kubuntu, Xubuntu). When you install Ubuntu, iptables is there, but it allows all traffic by default.

If you use hardy then you don´t need Firestarter because you have ufw.How to work with it see [here.]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html")

---

### Post by bryncoles on 2008-05-22
i upgraded form gutsy to hardy, and i was already using firestarter in gutsy. will it clash with ufw? should i remove one? just read the man pages for ufw and im not very clear on what it does, and how it does it, and if i should enable it by default if i have firestarter running!

any thoughts would be appreciated

---

### Post by pseudo-random on 2008-05-22
It won't clash since it's just a front-end for iptables (as already stated)
You could have a 100 front end clients and still be using good old iptables in the background. After all you can only use them one at a time. :)

---

### Post by fragos on 2008-05-22
True about the front end but the iptables rules created in Firestarter aren't loaded unless Firestarter is run. At least that was the case with 7.10 and before. Firestarter does give you an understandable GUI dynamic view of what's happening. 8.04 does install ufw which I believe is a command line rule generator.

---

