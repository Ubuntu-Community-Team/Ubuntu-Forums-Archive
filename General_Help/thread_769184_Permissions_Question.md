---
title: "Permissions Question"
date: 2008-04-26
forum: General Help
---

### Post by Sleaka J on 2008-04-26
I downloaded isoquake3 from [http://ioquake3.org/](http://ioquake3.org/) and it's a .run file.

When I either double click on it from a window or use terminal to run it using: "sh ioquake3-1.34-rc3.run" it wants to install into usr/local/games/ioquake3 but won't install because it has no write permission.

If I use the terminal to run "sudo sh ioquake3-1.34-rc3.run" it installs fine, but once I run it from the menu it never saves any config or user settings (again, because it has no write permission).

How do I solve this permissions problem? Do I change the permissions of the appropriate directory structure so that I can run as a user? Or should I run the game as superuser constantly? 

Note that this is less about the game itself and more to do with understanding how permissions work in Linux and find a way around it.

---

### Post by sisco311 on 2008-04-26
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

You can change the owner of /usr/local/games/ioquake3 directory:
```
sudo chown -R <username>:<username> /usr/local/games/ioquake3
``` A more sophisticate way is to create a new group like "quake3". Change the group of the directory(recursively) to "quake3". Change the permission of the directory(recursively) to 775. Add those users who are allowed to play the game to the group "quake3".

---

### Post by chrisccoulson on 2008-04-26
Hang on a minute, why would this game need write permissions on /usr/local/games/ioquake3 to save user settings? User settings will go somewhere in your home folder (perhaps ~/.ioquake3 or something like that).

Are you sure that you didn't run the game as root at the end of the installer, which caused it to create a user profile belonging to root in your home folder, which you can no longer write to?

---

### Post by geoff511 on 2008-04-26
Hi, have similar question - 
copied some files from my vista computer to ubuntu 8.04 computer.
says the permission & owner is nobody, Group is nogroup 
how do I change the owner to myself and my group ??

Thanks

---

### Post by Monicker on 2008-04-26
> **geoff511 said:**
> Hi, have similar question - 
copied some files from my vista computer to ubuntu 8.04 computer.
says the permission & owner is nobody, Group is nogroup 
how do I change the owner to myself and my group ??

Thanks

From a terminal:

```
sudo chown username.username filename
```

or all files in the current dir: 

```
sudo chown username.username *
```

...a whole dir and subdirs: 

```
sudo chown -R username.username /dir
```

---

### Post by Sleaka J on 2008-04-27
> **chrisccoulson said:**
> Hang on a minute, why would this game need write permissions on /usr/local/games/ioquake3 to save user settings? User settings will go somewhere in your home folder (perhaps ~/.ioquake3 or something like that).

Are you sure that you didn't run the game as root at the end of the installer, which caused it to create a user profile belonging to root in your home folder, which you can no longer write to?

You are correct, the user settings are kept in a ~/.q3a directory, but it is currently owned by root. The first time I tried to install it, it wouldn't install unless I used "sudo" which I did the second time, so that probably created the ~/.q3a directory and gave permissions to root which hasn't changed. I thought that similar to the Windows version, the settings would be kept in the isoquake3/baseq3 directory, but I was wrrrrrrr... misinformed.

> **sisco311 said:**
> 
You can change the owner of /usr/local/games/ioquake3 directory:
```
sudo chown -R <username>:<username> /usr/local/games/ioquake3
``` A more sophisticate way is to create a new group like "quake3". Change the group of the directory(recursively) to "quake3". Change the permission of the directory(recursively) to 775. Add those users who are allowed to play the game to the group "quake3".

Thanks, I'll try changing the permissions, however I am the only user of this machine so there is no real point of creating a group when I'm the only person who's going to play.

Edit: Sweet, that worked perfectly. I changed the permissions on both the isoquake3 and the .q3a directory and it works. Wouldn't have been able to do it without the help of both of you. You have my thanks.

---

