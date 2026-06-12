---
title: "Various Problems"
date: 2007-12-13
forum: General Help
---

### Post by Morgoroth on 2007-12-13
im new to all this, so apologies in advance for noob remarks.
im running version 7.04 and all was well for about a week when all these problems turned up.

first of all, my pc will suddenly go as laggy as hell when using firefox (was fine before, and my internet connection is fine) eventually not responding at all.

secondly, when trying to browse my files, opening anything causes the browser to close, only to reappear on my main folder.

thirdly, when trying to use the update manager, i get the message:

"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

when trying to use the Synaptic Package Manager, i get the message:

"E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open()failed, please report."

when i enter "dpkg --configure -a" into the terminal, it tells me i need superuser privilege, though i am the only user on this PC.

also, trying "sudo apt-get install -f" in the terminal gives me the same "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." message.

all this means i cant upgrade to 7.10, which i tried to do in the hope it would fix the other issues.

any ideas on what to do?

---

### Post by PLAY3ER on 2007-12-13
Hello, 

where i see you post that your new, i take it you don't know how to enter superuser mode , forgive me if you do, 

the password that you enter for login is you root password, root is superuser

so if you need to run dpkg --configure -a

run these in the terminal

sudo su (type you password)    

dpkg --configure -a  

that sure run it

as for the other problems someone else will need to reply as im trying to get 7.10 working my my Desktop and have never had these problems with 7.04, sorry i can't help more and good luck

---

### Post by viking777 on 2007-12-13
Try 

```
sudo dpkg --configure -a
```

Superuser is what you become when you use 'sudo' in Ubuntu.

---

### Post by PLAY3ER on 2007-12-13
thx viking, i haven't been able to use linux for a bit because of it restarting all of a sudden, and i forgot it'll just ask for the password

---

### Post by Morgoroth on 2007-12-13
thanks for the help. i tried that and now its telling me:

"dpkg --configure -a
dpkg: error processing compiz-plugins (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 compiz-plugins"

how does one go about fixing this?

---

### Post by mali2297 on 2007-12-14
You seem to be trapped in Catch-22. :-k

Try
```

sudo dpkg -P compiz-plugins
sudo dpkg --configure -a

```

---

