---
title: "cant access root folder in ubuntu 12.10"
date: 2012-10-29
forum: General Help
---

### Post by yasirmahmood on 2012-10-29
hey guys while using terminal i cant access my root directory because it says permission denied .more over if i manually browse to this folder from file system folder even than it doesnt open it 
since am not loged in as root user so one more problem is that through terminal i canot log in as root by typing root and giving password please help me

---

### Post by neu5eeCh on 2012-10-29
> **yasirmahmood said:**
> hey guys while using terminal i cant access my root directory because it says permission denied .more over if i manually browse to this folder from file system folder even than it doesnt open it 
since am not loged in as root user so one more problem is that through terminal i canot log in as root by typing root and giving password please help me

Not sure I completely understand the issue; but you won't be able to access "root" unless you are logged in as root.

In terminal: > sudo su It will then ask you for a password. From there, you can navigate to root. 

Or Alt+F2, then type > gksu nautilus or > gksu thunar if you're using Xubuntu.

---

### Post by snowpine on 2012-10-29
Welcome to the forums! Most of the time, you only need to worry about files in your /home folder. Files in the root folder (which sometimes people mean / and sometimes they mean /root .... which do you mean?) are locked down for a reason.

Can you tell us more about the task you are trying to accomplish so we can tell you the easiest and safest way?

---

### Post by yasirmahmood on 2012-10-30
well dear actually i installed wine and i wanted to check programe file folder which is located in root directory and i cauldn't access it thats why i asked it

---

### Post by Mark Phelps on 2012-10-30
It's been a long time since I used Wine (quit using it because it was largely a waste of time!) but from what I recall, Wine installed everything in a file structure starting with a hidden folder (.wine) inside your home folder.  I don't recall it installing anything directly under "/"  (root).  Perhaps someone with more recent experience can clarify this.

Also, you would do better posting Wine-related questions in the Wine subforum.  Folks there will see them and response faster than in this forum.

---

### Post by snowpine on 2012-10-30
I don't know what you mean by "check programe file folder."

To launch Wine from the terminal, you just type 'wine' plus the full filename of the windows executable. For example:

```
wine ~/Downloads/somegame.exe
```

Note that I have placed somegame.exe in my **home folder** so that my user has rights to it.

---

