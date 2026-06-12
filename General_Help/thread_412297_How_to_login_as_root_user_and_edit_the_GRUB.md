---
title: "How to login as root user and edit the GRUB ?"
date: 2007-04-17
forum: General Help
---

### Post by mocqueanh on 2007-04-17
I have installed Ubuntu yesterday.
After done, Ubuntu has install GRUB to master boot record and set ubuntu is the default OS of my PC.(i have XP and Ubuntu)
I want to make XP is my default OS.
Find the help document in Ubuntu, it says: edit the menu.lst in the grub folder to make XP is default OS.
But i cannot edit.
Ubuntu say i dont have permission.
I see the Properties of menu.lst, it belongs to root user.
But i cannot login as root user.
Ubuntu always say: You cannot login as root in this screen.
Please help me this problem.

---

### Post by ardchoille42 on 2007-04-17
> **mocqueanh said:**
> I have installed Ubuntu yesterday.
After done, Ubuntu has install GRUB to master boot record and set ubuntu is the default OS of my PC.(i have XP and Ubuntu)
I want to make XP is my default OS.
Find the help document in Ubuntu, it says: edit the menu.lst in the grub folder to make XP is default OS.
But i cannot edit.
Ubuntu say i dont have permission.
I see the Properties of menu.lst, it belongs to root user.
But i cannot login as root user.
Ubuntu always say: You cannot login as root in this screen.
Please help me this problem.

There is no need to ever log i as root. I have been running Ubuntu since Warty on 11 machines (5 of which are servers) and I have never seen a need to log in as root. We use [sudo]("https://help.ubuntu.com/community/RootSudo") in Ubuntu.

Log in normally, open a terminal, then type:
```

sudo vim /boot/grub/menu.lst

```
that will allow you to edit the grub list in the vim editor.

If you want a graphical solution, open a terminal and type:
```

gksudo gedit /boot/grub/menu.lst

```
That will open a root-enabled gedit so you can edit the file. There's no need to log in as root in Ubuntu.

---

