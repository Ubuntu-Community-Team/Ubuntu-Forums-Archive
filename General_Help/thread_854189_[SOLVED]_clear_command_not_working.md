---
title: "[SOLVED] clear command not working"
date: 2008-07-09
forum: General Help
---

### Post by Darkade on 2008-07-09
Hello, yesterday I bumped into a *lot* of trouble when trying to install xfce desktop, I desisted, but now some things won't work. I've solved most of them (or at least most of the problems I've notice) but one, or maybe more since other packages may depend on the same thing... My clear command,the one that clears the terminal screen LOL, won't work :S

this is what I get when running clear

```
ivan@icarus-laptop:~$ clear
The program 'clear' is currently not installed.  You can install it by typing:
sudo apt-get install ncurses-bin
bash: clear: command not found
ivan@icarus-laptop:~$ 

```

however ncurses-bin is installed :S
```
ivan@icarus-laptop:~$ sudo apt-get install ncurses-bin
[sudo] password for ivan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ncurses-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ivan@icarus-laptop:~$ 

```

Any ideas? thanks :D:D

---

### Post by ibutho on 2008-07-09
What happens when you enter
```
/usr/bin/clear
```
Have you tried reinstalling ncurses-bin?

---

### Post by ibuclaw on 2008-07-09
```
sudo aptitude reinstall ncurses-bin
```

Also, the key command **Ctrl+L** should clear the screen too.

Regards
Iain

---

### Post by Darkade on 2008-07-09
I had reinstalled it from a synaptic not from console, that worked.... I dunno why it didn't worked from synaptic.

thank you both :D

BTW /usr/bin/clear didn't existed anymore, it reappeared after the reinstall

---

