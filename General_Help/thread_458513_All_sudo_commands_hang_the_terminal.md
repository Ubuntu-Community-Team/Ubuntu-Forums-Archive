---
title: "All sudo commands hang the terminal"
date: 2007-05-29
forum: General Help
---

### Post by sparrowkc on 2007-05-29
Sudo seems to have quit working on my 7.04 Ubuntu install.  

For example, when I type "sudo gedit" to get a root terminal, it asks for my password, and then goes no further.  

I need a fix that doesn't require root privileges;)

---

### Post by taurus on 2007-05-29
Please use gksudo instead of sudo in that case.

```
gksudo gedit
```

---

### Post by Dylnuge on 2007-05-29
Does sudo work on non graphical packages, IE Nano? Also, remember that your password does not show while being typed.

---

### Post by sparrowkc on 2007-05-29
gksudo gedit doesn't seem to work,  gedit starts to launch but freezes,  and this is left in the terminal:
```

mark@mark-laptop:~$ gksudo gedit
(gedit:6097): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

sudo nano launches fine, it seems to work, but I'd like to be able to use gedit as root.

---

### Post by dfreer on 2007-05-29
> **sparrowkc said:**
> For example, when I type "sudo gedit" to get a root terminal, it asks for my password, and then goes no further. 
you need to type:
```
sudo su
```
to get a root access in a terminal, if that is what you mean. :confused:

EDIT:
Also, try:
```
sudo apt-get moo
```
If you see the cow sudo should be working...

are you sure this is an "sudo" thing and not an gedit thing?

---

### Post by sparrowkc on 2007-05-29
Cow works... 

If it is a gedit problem, nautilus has the same problem.  If the problem is with all the gui apps, how would I fix that?

---

### Post by dfreer on 2007-05-30
try running the command directly:
```
sudo /usr/bin/gedit
```

Is this a default install? Have you done anything major lately (installed beryl, drivers, updates)? Any info could potentially help.

Also, can you launch gedit from the command line as a normal user?

---

### Post by sparrowkc on 2007-05-30
Running directly doesn't work.
I installed several weeks ago, and I have been doing setup and fixing things as I find them, but I havn't done anything drastic.  I do everything the update manager suggests, but I don't remember if the problem started after an update or not.  I have edited xorg.conf for several things, but I think I did a clean job.  Just gedit works.

---

