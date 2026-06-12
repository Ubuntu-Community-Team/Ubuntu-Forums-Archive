---
title: "Bad Repository"
date: 2007-04-26
forum: General Help
---

### Post by manqueller on 2007-04-26
Hello,  I'm fairly new to Ubuntu and I have a few questions, my main problem is that I've added a repository to the package manager that apparently does not exist (either that or I type it incorrectly).  So when ever I go to package manger or I try to install updates I get an error message saying that there's a bad repository.  I can't figure out how to remove the bad repository.  I tried editing the sources.list file with the terminal, but it tells me I don't have permission.  I'm attaching a screen shot.

The other problem is how to keep track of my posts here.  I posted this question earlier and I can't find where that post is in the forum.



Manqueller

---

### Post by blamecanada on 2007-04-26
First you can go to System>Administration>Software soruces and uncheck the source in the Third party tab. If that doesn't work run this command:

sudo gedit /etc/apt/sources.list

then enter your password.

---

### Post by STREETURCHINE on 2007-04-26
post the out put of


     ```
cat /etc/apt/sources.list
```

and we will have a look

---

### Post by manqueller on 2007-04-26
> **blamecanada said:**
> First you can go to System>Administration>Software soruces and uncheck the source in the Third party tab. If that doesn't work run this command:

sudo gedit /etc/apt/sources.list

then enter your password.

Thanks!  I forget that I need to type sudo in order to get the permissions I need to make changes.  That fixed it.

---

### Post by STREETURCHINE on 2007-04-26
> **blamecanada said:**
> First you can go to System>Administration>Software soruces and uncheck the source in the Third party tab. If that doesn't work run this command:

sudo gedit /etc/apt/sources.list

then enter your password.

that should be 

     ```
gksudo gedit /etc/apt/sources.list
```

you should always use gksudo for all your graphical applications

---

### Post by blamecanada on 2007-04-26
What's the difference, I've seen both but never really knew the difference between the two.

---

### Post by STREETURCHINE on 2007-04-26
Root Access with sudo and gksudo
ubuntu unlike many distributions does not normally have a user accessible root account. You are supposed to use one of these two commands when you need root access. sudo is for when you are in the terminal and need root access and gksudo is when you are in the GUI and need root access, for example you can press alt+f2 and type "gksudo appname".

If you need a root account for some reason, an easy way to do it is to open up the user account manager by pressing alt+f2 and typing gksudo users-admin.

---

