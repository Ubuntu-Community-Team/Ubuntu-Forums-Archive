---
title: "Login trouble"
date: 2007-09-24
forum: General Help
---

### Post by ephesius on 2007-09-24
Hi everyone, I'm having some login trouble, whenever i try to log in the system locks up. I think there is something wrong with my home directory but its only mine, i can log in from other user names. When I go in through the console and try to use ls in my home directory it locks up as well. Once when I used ls I managed to get a segmentation_fault error, other than that I have no idea what is happening.

---

### Post by jamvegan on 2007-09-24
First of all, I'm sorry to say that I have no idea what the problem is.  Still, I'm willing to throw some ideas at you and you can do with them what you will. :-)  (I don't know what your experience level is, so apologies if anything is either too obvious or too opaque.)  You say that you are unable to list your home directory.  I assume that you mean the contents of it.  Are you able to do a long listing on the directory itself?
```
ls -ld /home/username
```
The output should resemble this:
```
drwxr-xr-x 57 username username 4096 2007-09-24 20:28 /home/username
```
Do you know that it is possible to view the contents of a directory with vi?  Directories are just a special kind of file in UNIX/Linux, so you can get all of the information that you would get from "ls -a /home/username" by doing:
```
vi /home/username
```
(If you are unfamiliar with vi, then I would suggest using just the up and down arrows on your keyboard to navigate through the file, and :q<return> to exit vi when you're done.)

By the way, are you able to log into a terminal session as yourself, or were you trying to list your home directory while logged in as another user?  If you were able to login as yourself, what directory were you in upon login?

I hope that something here helps you to at least narrow down the problem.  Best of luck!

---

