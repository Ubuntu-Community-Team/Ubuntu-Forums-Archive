---
title: "using su when running from external hard drive"
date: 2020-07-03
forum: General Help
---

### Post by kolin-w on 2020-07-03
I have Ubuntu 18.04.01 LTS running from an external hard drive.

Anyone know how I can run as a super user? I want to copy files from the computer onto the external drive, and it refuses.

I have set all the files and directories I can access with sudo to executable, readable and writeable.

Colin

---

### Post by TheFu on 2020-07-03
Ubuntu uses the sudo command.

Running any gui programs using sudo will often lead to all sorts of problems, some will prevent future logins.

As for the external drive access, there are a number of considerations depending on where it is mounted and which filesystem it has.
**df -Th** will show that.
Running a **mount** command will show the options for each mount as well.

With that data, we can solve the problem.  However, if that external storage is using a non-Linux file system, the necessary commands and setting are much more hassle.

We want to solve this the correct way, not give you a gun, have you point it at your foot, hand, or head and walk away. By the specific question, I've made some assumptions that knowledge concerning permissions and mounts aren't complete.

---

### Post by coffeecat on 2020-07-04
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by kc1di on 2020-07-04
install the following in terminal type ```
sudo apt install nautilus-admin
``` when that is finished you will find a right click menu entry that says ```
open as administrator 
``` you can use this to copy and paste any file to where ever you want it.  But be careful you could damage your system. if you move a file to the wrong location.  Good luck.

---

### Post by ActionParsnip on 2020-07-04
Just mount the partition properly to give your user access. What file system does the destination storage use please?

---

### Post by Impavidus on 2020-07-04
> **kolin-w said:**
> 
I have set all the files and directories I can access with sudo to executable, readable and writeable.


What does that mean? It sounds like a bad idea.

---

