---
title: "Constraining Folding@Home to one folder?"
date: 2006-11-13
forum: General Help
---

### Post by teiresias on 2006-11-13
Hi all,

I've been running folding@home on my Edgy install pretty well for a while, but one thing is bugging me.  I downloaded the .exe from the Stanford site and placed it in a folder in my home directory, so it's basically in
/home/username/Folding@Home

I then put a menu item in my bar so I can start it from there and the command I'm using is:
/home/username/Folding@Home/./FAH502-Linux.exe

This seems to all work fine, except it creates a work directory and places the client.cfg file in /home/username instead of in /home/username/Folding@Home

Actually, it seems to create them in both, but only seems to use the onees in /home/username, because if I delete those and start it again it looses its configuration and recreates everything in /home/username.

Does anyone know how I can constrain it to use the work directory and create the other files in /home/username/Folding@Home.  The stanford faq says the -local option has no use in the Linux version of the client, so I'm at a loss for what to do.  Thanks everyone.

---

### Post by jpkotta on 2006-11-16
F@H creates it's files in whatever the current directory is for the shell that called it, which may not be the directory that the executable is located in.  For example:

```
cd 
/path/to/FAH502-Linux.exe
```
and 
```
cd /foo
/path/to/FAH502-Linux.exe
```
will have the client write it's files to $HOME and /foo, repectively.  

See the wiki page for a solution: [https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

---

