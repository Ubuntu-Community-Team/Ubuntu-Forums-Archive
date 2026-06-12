---
title: "Change graphics in GNOME"
date: 2015-05-25
forum: General Help
---

### Post by hailholyghost on 2015-05-25
Hello,

I like to use gedit for writing my C programs.  My work computer shows the "GOOD" image and my laptop shows the "BAD" image.

I do not like the "BAD" version at all, I cannot find how to use the File/Edit/whatever. I don't know how this came to be.
[ATTACH=CONFIG]262200[/ATTACH]

both computers have identical GTK version
```
con@e:~$ dpkg -s libgtk-3-0|grep '^Version'
Version: 3.14.12-0ubuntu2
```

How can I convert my laptop's image "BAD" to "GOOD"?

thanks,
-DEC

---

### Post by nerdtron on 2015-05-25
what version of Ubuntu is on the "good" and on the "bad"?
```
lsb_release -a 
```

Sorry, I'm using Xubuntu, so the command that I gave will show your OS version so that others can give you a better answer.

---

### Post by hailholyghost on 2015-05-25
> **nerdtron said:**
> what version of Ubuntu is on the "good" and on the "bad"?
```
lsb_release -a 
```

Sorry, I'm using Xubuntu, so the command that I gave will show your OS version so that others can give you a better answer.

both laptop and work computer give:

```
con@laptop:~/DNA_Methylation$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid

```

---

### Post by grahammechanical on 2015-05-25
My guess is that the "good" machine is running Ubuntu 15.04 with Unity and the "bad" machine is running Ubuntu Gnome in Gnome Flashback session (Or Gnome Classic) and Gedit on the "bad" machine is the Gnome version of Gedit. Whereas, the Gedit in Ubuntu Unity is a Ubuntu modified Gedit.

Of course, I have not tested this by installing Ubuntu Gnome 15.04 but I know that we get Applications Places in a Gnome Flashback session and not in a Unity session. And that utilities like Gedit are modified to fit the Unity design scheme. 

Look at these screenshots of Gedit as the Gnome developers designed Gedit

[https://wiki.gnome.org/Apps/Gedit/Screenshots](https://wiki.gnome.org/Apps/Gedit/Screenshots)

The "bad" machine is running the unmodified version of Gnome Gedit. And the "bad" machine is your laptop.

Regards.

---

### Post by hailholyghost on 2015-05-25
both are running GNOME.

---

