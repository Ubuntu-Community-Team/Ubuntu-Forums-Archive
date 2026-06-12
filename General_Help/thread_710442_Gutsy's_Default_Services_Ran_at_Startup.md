---
title: "Gutsy's Default Services Ran at Startup"
date: 2008-02-28
forum: General Help
---

### Post by notwen on 2008-02-28
Anyone able to give me a list of services that Gutsy runs by default on a fresh install?  I'm wanting to go through and pick out the services that would not affect my daily usage to speed up boot time.  When I get home, I'll post back attaching my boot chart.  There are multiple threads on this, but most are out-dated and do not go into the amount of detail I was hoping for.  (ie. list of services and maybe a short description of what they do)

---

### Post by p_quarles on 2008-02-28
Two things you can look at. First:
```
ls /etc/rc2.d
```
Scripts beginning with "S" are initiated when the system enters runlevel 2 (the default for normal Ubuntu usage). This will give you an idea of what is started with the system.

Second, there's a very handy ncurses tool for tweaking these processes:
```
sudo apt-get install sysv-rc-conf
```
Run this from the terminal with sudo, and you will be able to configure which services start up. Processes that are initiated in runlevels 2-5 are the ones you want to look at. I would advise against messing with any process unless you're sure what it does. Some things, though, are fairly obvious. You don't need to initiate Bluetooth support if you don't need it (though Ubuntu does, by default), and you don't need to load the Nvidia kernel if you're using an Intel graphics card.

---

### Post by notwen on 2008-02-28
Thanks.  I've got it downloaded and will look through them tomorrow morning.  Do you know of any document or site that may offer a short description on each service?  =]

---

### Post by pointone on 2008-02-29
The files in /etc/rc*.d are all just shell scripts. Simply open one in your favourite editor for a description and to see exactly what's going on.

man is also useful.

---

