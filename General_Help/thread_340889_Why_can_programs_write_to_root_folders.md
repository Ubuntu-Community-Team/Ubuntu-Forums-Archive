---
title: "Why can programs write to root folders?"
date: 2007-01-17
forum: General Help
---

### Post by tweedledee on 2007-01-17
Why can I launch a program as a non-root user that then can write files to a root-owned folder?  For example, all the games in gnome-games write their score files to /var/games, which is a root-owned folder, and all the files are owned by root.  Yet somehow the programs are allowed to modify those files, even though I cannot if I try to do so manually.  I use the eample of the games because they are a standard part of the Ubuntu package and don't prompt me for a password if I launch them.

I probably just need a pointer to a primer on the nuts and bolts of how permissions actually work under Linux, but this behavior distubs me a little - it suggests that the capability exists for programs to have total control over my system despite the supposed protection in the permissions system.

---

### Post by taurus on 2007-01-17
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by az on 2007-01-17
> **tweedledee said:**
>   For example, all the games in gnome-games write their score files to /var/games, which is a root-owned folder, and all the files are owned by root.  Yet somehow the programs are allowed to modify those files, even though I cannot if I try to do so manually.  

I don't know specifically what the under-the-hood details are for gnome-games, but there are a number of processes that Gnome runs as root before you even log in.  Usually, they involve security issues (like GDM being able to launch a session as any user that can authenticate) or message-passing.  It's probably a feature that the way the gnome games keep score allows for users to see all the other user's high scores.

So, I don't think that the game itself writes to that file, but passes a message to a process that can.

---

### Post by aysiu on 2007-01-17
Prevents you from tampering with the high score another user achieved?

---

### Post by treyh0 on 2007-01-17
You are in the "games" group.  The files in /var/games are have a group ownership set to "games" with read-write access.

> **tweedledee said:**
> Why can I launch a program as a non-root user that then can write files to a root-owned folder?  For example, all the games in gnome-games write their score files to /var/games, which is a root-owned folder, and all the files are owned by root.  Yet somehow the programs are allowed to modify those files, even though I cannot if I try to do so manually.  I use the eample of the games because they are a standard part of the Ubuntu package and don't prompt me for a password if I launch them.

I probably just need a pointer to a primer on the nuts and bolts of how permissions actually work under Linux, but this behavior distubs me a little - it suggests that the capability exists for programs to have total control over my system despite the supposed protection in the permissions system.

---

### Post by tweedledee on 2007-01-18
> **treyh0 said:**
> You are in the "games" group.  The files in /var/games are have a group ownership set to "games" with read-write access.

Actually, I'm not.  There is a "games" group available, but only root is a member on my system.  Or at least, only root can assign ownership to games, and I don't appear to be able to edit that group.  And the /var/games folder is set to a group of "root" as well.  In addition, if I were a member of a group with read/write permissions, shouldn't I always be able to read/write, not just when running a program?

And if it's just a matter of passing off the write command to another process, is it a process that ONLY accepts write commands from certain programs, or from almost anything?  Either way, I'd worry about spoofing, allowing arbitrary programs to have root write access, unless there is some fairly tight control behind the scenes.

---

### Post by taurus on 2007-01-18
If you look at the ownership of most files on your system, owner can read/write/execute, group can read/execute, and everybody else can read/execute.  Therefore, if you can run a program without being root doesn't mean you can write or modify it!

If you want to add yourself to group games, run

```
sudo adduser **username** games
```
(where **username** is your login name...)

---

### Post by tweedledee on 2007-01-18
> **taurus said:**
> If you look at the ownership of most files on your system, owner can read/write/execute, group can read/execute, and everybody else can read/execute.  Therefore, if you can run a program without being root doesn't mean you can write or modify it!

If you want to add yourself to group games, run

```
sudo adduser **username** games
```
(where **username** is your login name...)

Understood on the read/write/execute issue.  And I was being lazy on the modify - "games" doesn't show up in the GUI.  Anyway, my point is that if I run (for example) same-gnome (which does not trigger sudo or gksudo, hence no password prompt), it does in fact write a score file in /var/games, which is root:root owned.  Therefore, despite having no write permission, I am (indirectly) writing to that directory.  I just don't understand why or how this is being allowed.

Note that I don't really care about the games, this is just an example for a broader question - how does one write to a folder despite not having the right to do so?  This is (apparently) happening, so it's obviously possible.

---

### Post by taurus on 2007-01-18
As the azz man already explained in his reply, some processes would call up root to write the output, whatever that might be, to system log.  For instead, if you play around and somehow crash X, there is a error message in /var/log/Xorg.0.log but if you look at the permission of that file or even /var/log, only root can write to it!!!  How could that be?

---

### Post by tweedledee on 2007-01-18
> **taurus said:**
> As the azz man already explained in his reply, some processes would call up root to write the output, whatever that might be, to system log.  For instead, if you play around and somehow crash X, there is a error message in /var/log/Xorg.0.log but if you look at the permission of that file or even /var/log, only root can write to it!!!  How could that be?

I found the answer elsewhere.  It boils down to the SUID feature of permissions - basically, most of the gnome-games are set to execute with root permission (permissions are -rwxr-sr-x).  This is also true for the /var/log files, and presumably most other instances of writing as root while a user.  I now understand the (deliberate) gaping hole in the linux security system.  In the event someone unfamiliar with this feature is reading, the "s" flag on permissions basically says "execute this file as the owner, not as the user executing the command."  In short, it is a method for users to perform activities or access areas that ordinarily only root can get at - without any password protection.

It does bother me that a default package in Gnome is using this major security hole to do something as trivial as keep a high score from being edited by a user (as aysiu pointed out), but that's something to take up elsewhere.

---

### Post by Ragazzo on 2007-01-19
Actually they have setgid. So they're not executed as root but have the group games when run.

---

