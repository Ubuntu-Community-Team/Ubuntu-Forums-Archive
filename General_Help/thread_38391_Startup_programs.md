---
title: "Startup programs"
date: 2005-05-31
forum: General Help
---

### Post by Hardi on 2005-05-31
Hy.
I added a command to System>Preferences>Sessions>Startup programs tab
The command was "firestarter"
But when I logged in it said that I have to be a root user to use this program. Although if I execute the Root terminal and type "firestarter", the program will start.
Please help.

---

### Post by Alexander Kirillov on 2005-05-31
[QUOTE=Hardi]Hy.
I added a command to System>Preferences>Sessions>Startup programs tab
The command was "firestarter"
But when I logged in it said that I have to be a root user to use this program. Although if I execute the Root terminal and type "firestarter", the program will start.
Please help.[/QUOTE]
 A better choice would be to have firestarter started at boot, not at login time. To do this, you would have to create a script to add in /etc/init.d

---

### Post by [pl]ice on 2005-05-31
firestarter provies answer for that, in the manual.
  if u compiled yourself, then there is a script : fedora.init or something like that, copy it, to etc/init.d then rename to firestareter.init

edit : /etc/sudoers

and put at the end:

ur_username ALL= NOPASSWD: /usr/local/bin/firestarter

that will do it.

note, if u have deb it , then the script will be installed automatically, then jsut edit sudoers

works for me.

---

