---
title: "[SOLVED] Be Root everywhere in GUI mode"
date: 2008-01-22
forum: General Help
---

### Post by dethredic on 2008-01-22
Ok, I am doing some stuff with a server, I need to be able to move, edit and delete files in places where I don't have permission. I am in GUI mode because I am much more comfortable and efficient there. So, is there anyway so that I can always have root access when moving files and deleting files with drag + drop and rightclick->move to trash and other such GUI commands.

---

### Post by kellemes on 2008-01-22
> **dethredic said:**
> Ok, I am doing some stuff with a server, I need to be able to move, edit and delete files in places where I don't have permission. I am in GUI mode because I am much more comfortable and efficient there. So, is there anyway so that I can always have root access when moving files and deleting files with drag + drop and rightclick->move to trash and other such GUI commands.


Is this what you mean?
```
gksudo nautilus
```

---

### Post by dethredic on 2008-01-22
Yes, but is there any way I can make it so that just auto happens? It will be a pain to type that in every time.

---

### Post by nemilar on 2008-01-22
The above reply will work..it will give you Nautilus with root permissions.  But it can't be emphasized enough how dangerous this is!!  If you accidentally move something, or delete something, or rename something, or god knows what, you're going to be kicking yourself for a very long time.

---

### Post by kellemes on 2008-01-22
> **dethredic said:**
> Yes, but is there any way I can make it so that just auto happens? It will be a pain to type that in every time.


Just create a menu-item with this instruction..
You can than put it on the desktop or panel if you wish..

---

### Post by Tanjer1588 on 2008-01-22
you could allways just enable root login from your login screen and login as root, if you go to system-->admin(i think)-->Login then go to the security and click the box with enable root login

---

### Post by kellemes on 2008-01-22
> **Tanjer1588 said:**
> you could allways just enable root login from your login screen and login as root, if you go to system-->admin(i think)-->Login then go to the security and click the box with enable root login


Brrr.. better not.

---

### Post by Tanjer1588 on 2008-01-22
> **kellemes said:**
> Brrr.. better not.

Whats the risks of doing that?

---

### Post by dethredic on 2008-01-22
I am the only one that will ever touch this computer, unless someone breaks into my house...

EDIT: is root = local system administrator?

---

### Post by aysiu on 2008-01-22
> **dethredic said:**
> Yes, but is there any way I can make it so that just auto happens? It will be a pain to type that in every time.
Or, better yet, create a keyboard shortcut for the command.

> **dethredic said:**
> Ok, I am doing some stuff with a server > **dethredic said:**
> I am the only one that will ever touch this computer, unless someone breaks into my house... These two statements contradict one another. If you are running a server, logging in as root is a security risk.

---

### Post by rosegarden78 on 2008-01-22
In Blackbox Ubuntu, Fluxbox and/or Xubuntu - you launch the file manager as superuser.  If you're using Ubuntu you're using Nautilus.  Try this:

1) Download kde, xfce, fluxbox and blackbox from the repositories and logout of session.
2) Select Blackbox as Default Session on login screen
3) Right click mouse at Xterm type:

a) nano go

#!/bin/sh
#go script
#--------------
xgamma -gamma 0.75
kicker
gksudo nautilus

b) sudo chmod +x go

c) bash go OR ./go

Using gksudo to launch nautilus should work.  You could also try:

1) Create launcher on desktop
2) Under command type: gksudo nautilus

---

### Post by dethredic on 2008-01-22
I will just use the launcher.

Thanks guys.

---

### Post by atlien on 2008-01-25
Where are the technical writers who use Ubuntu???

I know everyone means well (at least I believe they do) but these explanations really could be more useful to us novices.  And I don't mean idiots.  But moderately intelligent people who just don't have Linux experience

---

### Post by stchman on 2008-01-25
> **dethredic said:**
> Ok, I am doing some stuff with a server, I need to be able to move, edit and delete files in places where I don't have permission. I am in GUI mode because I am much more comfortable and efficient there. So, is there anyway so that I can always have root access when moving files and deleting files with drag + drop and rightclick->move to trash and other such GUI commands.

Logging in as root is not advisable at all.  You run a lot of security risks.  Just use sudo and gksudo whenever you need root privileges.

---

