---
title: "problem logging into root terminal"
date: 2005-03-30
forum: General Help
---

### Post by lifesayko on 2005-03-30
Hi, I'm new to using linux, and am just starting to learn the commands.
   I've created a new user to use, so as not to mess up root, and just now I tried logging into root terminal to shutdown, and it didn't take my password and said  error: failed to run /usr/bin/x-terminal-emulator as user root: Child terminated with 1 status

can anyone tell me what's going on? it's looks scary... :confused: 
    thx, all the best

---

### Post by DJ_Max on 2005-03-30
Your problem was creating another user when there was no need to. In ubuntu, by default there is no root account, just the first user as root prvileges. Login as the account created during your install.

---

### Post by lifesayko on 2005-03-31
Well, since it's the first time I'm using linux, I decided to do the course on linux.org, [http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html) ,  and there it said that you should never work as root, because if you mess something up bigtime, it's done.
    Also, I didn't just switch to ubuntu linux because I wanted to use linux and not windows, but also I wanted to learn how to use and modify linux and eventually program......is ubuntu a bad choice for this?

---

### Post by DJ_Max on 2005-03-31
I don't think you understand, that guide targets Debian, you are using Ubuntu. Ubuntu sets up the first account differently. You DO NOT have an account name "root". Other distros, the first account is root, NOT Ubuntu.

Disregard that section of that guide.
If you want to modify and program, Ubuntu, as with any other Unix/Linux OS, it'll work fine

BTW, it says you should login as root, but you WILL HAVE to work with root privleges to install programs.

---

### Post by matthieufecteau on 2005-05-03
Maybe (I say maybe) the solution of your problem could be in the second post of this thread : [http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback](http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback)

---

