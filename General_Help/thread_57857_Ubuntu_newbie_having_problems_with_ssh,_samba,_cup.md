---
title: "Ubuntu newbie having problems with ssh, samba, cups"
date: 2005-08-18
forum: General Help
---

### Post by bogoliubov on 2005-08-18
Hello there. I just switched from Fedora 4 to Ubuntu. I've using Linux for about a year, so I'm still quite the newbie...

Anyway; my problem is that I can ssh from my ubuntu-machine, nut not to it! I have installed Firestarter and opened port 22. The computer is in a LAN connected to the internet through a (netgear) router. On the same LAN is an iBook running Tiger.

I can ssh from the PC to the ibook, but not the other way around! Have I missed some settings excdept from firestarter? If I want to disable all firewalls in ubuntu, how can I do that? Since the router has a firewall that should be enough...

Oh, another thing! How do I share my files using samba? Anyone knows a good howto or something? I can mount the ibook manually, but would like to share the files on the PC as well...

I have a printer connected to the PC. Should i use samba or cups to share it with the ibook? Any advice?

---

### Post by adwait on 2005-08-18
To open the SSH port on your Ubuntu machine, you should try
```
sudo /etc/init.d/ssh start 
```

---

### Post by bogoliubov on 2005-08-18
Thanks but it doesn't work. Obviously I'm missing something...
This is the output I get:
:~$ sudo /etc/init.d/ssh start
Password:
sudo: /etc/init.d/ssh: command not found

Any ideas?

---

### Post by adwait on 2005-08-19
Try this,
```
 sudo apt-get install openssh-server 
```

That will install the ssh server, then try the command I gave you before.

---

### Post by zek725 on 2006-10-19
> **adwait said:**
> To open the SSH port on your Ubuntu machine, you should try
```
sudo /etc/init.d/ssh start 
```

yup. easily done in ubuntu. How do you reset that in windowsXP? 

I ran Putty for remote login from XP to Ubuntu. During/After the session, samba networking won't work in the Ubuntu machine. Only solution I had working was to relogin to the XP machine. It's troublesome if I had many files opened there so I am looking of a convenient way in XP just like in Ubuntu.

---

