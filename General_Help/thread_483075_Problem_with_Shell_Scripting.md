---
title: "Problem with Shell Scripting"
date: 2007-06-24
forum: General Help
---

### Post by NuNn DaDdY on 2007-06-24
I'm trying to read an introduction to shell scripting and when I try to put in a alias command I cannot find the file which I'm suppose to put the alias command in with my text editor.  I'm looking for .bash_profile and website says it should be in my home directory but when I look there I'm unable to find it when I try to open the file via the "gedit & .bash_profile" command.   Does anyone have a solution to this.  Thank you

---

### Post by mattg89 on 2007-06-24
try:
```
sudo gedit ~/.bash_profile
```

---

### Post by aJayRoo on 2007-06-24
The '.bash_profile' file used to be located in the home directory but I have noticed in recent versions of Ubuntu that it is no longer used. Instead you may place alias commands directly into the '.bashrc' file which is a hidden file located in your home directory. A sample command to edit this file is:
```
gedit ~/.bashrc
```
Note that root (sudo) permissions are not necessary to edit this file since it only affects your user. Hope that helps.

---

### Post by NuNn DaDdY on 2007-06-24
Thanks for the help, also what does the "~/" in front of .bashrc do?

---

### Post by Old *ix Geek on 2007-06-24
> **NuNn DaDdY said:**
> Thanks for the help, also what does the "~/" in front of .bashrc do?That's just UNIX/Linux shorthand for "your home directory."  So if your home directory is **/home/john**, you can refer to it as **~/** from anywhere in the directory structure.  If you're already in your home directory, just leave it out!  (In other words, **gedit .bashrc** as opposed to **gedit ~/.bashrc**)

---

