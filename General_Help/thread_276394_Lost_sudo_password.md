---
title: "Lost sudo password?"
date: 2006-10-12
forum: General Help
---

### Post by Joey French on 2006-10-12
Hi all,
was just trying to set up Samba and somehow during the configuration process, I have messed up my password. When I try to use sudo, I get this:
```
joey@cnidaria:~$ sudo synaptic
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0
joey@cnidaria:~$

```

Upon going to my /etc/sudoers file (I have no idea why, just to see what's going on), I see a blank document. I am able to log in with my password, but I cannot su, sudo, kdesu or otherwise. Anyone know how I can get this back on track, or where to start?
I believe that all this trouble came about because I issued these two commands to try to set Samba passwords:

```
sudo passwd -a joey
smbpasswd -a joey
```

---

### Post by aysiu on 2006-10-12
Try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Joey French on 2006-10-13
Nice! That was easier than I expected. Interestingly, some garbage in my new edgy install's terminal got written to the file /etc/sudoers. Don't have a clue how! Anyway, I removed the garbage and saved, and voila, sudo is back in action. 

Weird.

Thanks a ton,
Joey

---

