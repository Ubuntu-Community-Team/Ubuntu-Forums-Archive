---
title: "How do I change the write permission on /usr/local/bin"
date: 2008-04-25
forum: General Help
---

### Post by piromedic on 2008-04-25
I am trying to install a program.  When I install it I get a message that I have no write permission on /usr/local/bin.  I have tried to change the write permission and it tells me that I do not own the folder.  Can anyone point me in the write direction? 


Don

---

### Post by olskar on 2008-04-25
If you are installing the program from a terminal, write sudo in front of the install command

---

### Post by piromedic on 2008-04-25
I was not in terminal, but I tried it in terminal and I get command not found

> **olskar said:**
> If you are installing the program from a terminal, write sudo in front of the install command

---

### Post by Ziggy72 on 2008-04-25
Perhaps you should tell us what program you are trying to install and how you're trying to install it. The more information you give, the easier it is for somebody to suggest a sensible solution to the problem.

---

### Post by piromedic on 2008-04-25
I am trying to install American Army.  I down loaded the program into a file on my desktop.  Then I clicked the button armyops250-linux.run.  It starts the install process and asks if I want to install into /usr/local/bin.  I clicked yes and I get the message that I do not have write permission on that file.

---

### Post by ykpaiha on 2008-04-25
the command for changing the right is:
chmod as root
by example changing recursively with write read rights on (it's an example replace by your own)/usr/locale/i_love_you_sometime/
it gives
chmod -R 777 /usr/....
-R is fot the recursive all the file and folders inside will get the right you will give
777 are the read/write right for any one!
a bit dangerous anyway look for the rights on google (from 000 to 777)
I personaly use /opt for this purpose to avoid any trouble in /usr
but fot you install just do it as root it will be sufficient
good luck

---

### Post by newb1e on 2008-04-25
> **piromedic said:**
> I am trying to install American Army.  I down loaded the program into a file on my desktop.  Then I clicked the button armyops250-linux.run.  It starts the install process and asks if I want to install into /usr/local/bin.  I clicked yes and I get the message that I do not have write permission on that file.

in terminal, go to the folder you have the file then type:
```
sudo ./armyops250-linux.run
```
Then just type your password.:popcorn:

---

