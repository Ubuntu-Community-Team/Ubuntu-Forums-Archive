---
title: "Can't view entire contents of /"
date: 2007-02-14
forum: General Help
---

### Post by acranox on 2007-02-14
When I open the File Browser and navigate to the root directory, I can't see all the directories.  I'm assuming that it's basically limited what I can view because I'm not root, but can I change this so I can view everything even if I can't change it?  I'm running 6.10
The permissions are the same on everything, everyone has read access to the directories, but I can only view /home and /media.

thanks.
--Peter

---

### Post by dcstar on 2007-02-14
> **acranox said:**
> When I open the File Browser and navigate to the root directory, I can't see all the directories.  I'm assuming that it's basically limited what I can view because I'm not root, but can I change this so I can view everything even if I can't change it?  I'm running 6.10
The permissions are the same on everything, everyone has read access to the directories, but I can only view /home and /media.

thanks.
--Peter

```
gksudo nautilus
``` should launch a file browser with root privileges, you can create a Launcher with this and put it in you Panel (if you like).

---

### Post by masteryurez on 2007-02-15
> **acranox said:**
> When I open the File Browser and navigate to the root directory, I can't see all the directories.  I'm assuming that it's basically limited what I can view because I'm not root, but can I change this so I can view everything even if I can't change it?  I'm running 6.10
The permissions are the same on everything, everyone has read access to the directories, but I can only view /home and /media.

thanks.
--Peter

I just have that problem in my own computer. I could just see 2 directories: /home and /media.

Solution:
The problem is that the other directories just are hidden. 
Just type **CTRL + H** in the **/** directory and you will see your directories. 

But listen here.
It is a new file called **.hidden** in the **/** directory. Just delete the file and the directories will never be hidden again. 

//Good Luck Linux User :)

---

