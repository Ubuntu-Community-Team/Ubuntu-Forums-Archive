---
title: "Having trouble adding a program to start up with Sessions manager"
date: 2007-08-21
forum: General Help
---

### Post by bennyj on 2007-08-21
HI,Just to let ya know I have added plenty of programs to start up using >System>Preferences>Sessions.My problem is that after i add it and click ok,the newly added session dissappears.Is anyone else having this problem.No matter what I try it will not stay after I add it.Im using Fiesty.Thanks

---

### Post by wormser on 2007-08-21
I have not had an issue with adding programs.  What is the command you are trying and have you tried a different command?

---

### Post by Trosky on 2007-08-21
I solved in these way. hope it's useful for you
$ sudo nautilus
Ctrl + h
/home/username/.config
Now change the permission of folder "autostart": add it to the admin group and make permission of create and delete files

Arkan

---

### Post by bennyj on 2007-08-21
> **wormser said:**
> I have not had an issue with adding programs.  What is the command you are trying and have you tried a different command?

I am just trying to add a simple script at start up that delays conky for 10 seconds then starts conky.I have made sure the script is executable and double checked the typed in command and still nothing.what im typing in does work.I can double click the script and it executes fine.I just cant get the session I add to stay put.as soon as i click on ok and it closes(sessions that is) it disappears.I have never had this happen before.

Thanks Arkan I will try that out.just wish this would take.

---

