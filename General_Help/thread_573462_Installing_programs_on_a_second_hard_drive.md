---
title: "Installing programs on a second hard drive"
date: 2007-10-11
forum: General Help
---

### Post by cfehunter on 2007-10-11
Hi, I've had Ubuntu for just over a week now and I've just gotten rid of windows vista off my second hard drive. I used Gparted to format my other hard drive with the ext 3 file system.

Can anybody tell me how I install programs onto my second hard drive please?

Thanks in advance.

---

### Post by kellemes on 2007-10-11
You want only program to be installed on a separate partition?
May I ask why you want to do that?

---

### Post by cfehunter on 2007-10-11
it's not just a seperate partition, i have two physical hard drives, and by default ubuntu installs programs to my home folder.

---

### Post by kellemes on 2007-10-11
So basically you want your home-folder on it's own partition?
You could have done that from the installer -> create partition on HD2 -> mount /home to this partition.

Anyway, now this link may help.
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

Edit: Doing stuff like this screams for making a backup first. :popcorn:

---

### Post by cfehunter on 2007-10-11
thanks for the quick response. 
What i was going for was being able to run programs off of both hard drives, if that's even possible under ubuntu. 
This is my first linux distribution and i've used nothing but windows before it.

---

### Post by kellemes on 2007-10-11
Sorry, don't understand what you mean actually.
Can you explain please?

---

### Post by cfehunter on 2007-10-11
sorry, here's my question put in a better way.

Is it possible to install programs outside of your home directory, and if so, how?

---

### Post by kellemes on 2007-10-11
First.. Programs are not installed in /home.. it's mostly program-settings that (may) reside there.
Programs leave crap allover the system.

You can move /home to another partition ofcource. This gives you the option to backup/restore your settings in case of trouble.
You can install program(settings) in another folder simply by changing your /home folder.. this basically means you rename/move your /home folder.. so it's still your /home folder. :popcorn:
Understand programs will need your /home folder!
The renaming of /home folders I don't know about because I think it can only give trouble, never done it myself.

---

### Post by cfehunter on 2007-10-11
thanks for explaining that. :)

---

