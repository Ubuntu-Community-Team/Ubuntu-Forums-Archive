---
title: "Huh? cd command not found"
date: 2007-07-23
forum: General Help
---

### Post by Thrasyllus on 2007-07-23
I try to cd to a restricted directory as user and the system tells me permission is denied. Fair enough. Then I sudo the same command and get the message "sudo: cd: command not found". What gives? I can sudo chmod the directory and whatever files I need, and then the user can access them; but cd remains invisible to the superuser. What did I do wrong?

---

### Post by bbzbryce on 2007-07-23
> **Thrasyllus said:**
> I try to cd to a restricted directory as user and the system tells me permission is denied. Fair enough. Then I sudo the same command and get the message "sudo: cd: command not found". What gives? I can sudo chmod the directory and whatever files I need, and then the user can access them; but cd remains invisible to the superuser. What did I do wrong?

While I can't completely explain why it doesn't work try doing:

sudo -s

This will give you root access, then cd into the folder of your liking.

---

### Post by aysiu on 2007-07-23
```
sudo -i
cd */path/to/directory*
``` could also work

---

### Post by meatpan on 2007-07-23
> **Thrasyllus said:**
> I try to cd to a restricted directory as user and the system tells me permission is denied. 

Just curious, why are you trying to sudo a 'cd' command?  The reason I ask is because sudo is typically used in a single command, and cd'ing doesn't really accomplish much.  Usually someone would cd to a folder and *then* perform a task.  Frequently, you can use absolute paths rather than cd'ing to reference a file.  (absolute paths are paths starting with the root directory, '/'., i..e.  ~userid/file.txt is a relative path, whereas /home/userid/file.txt is absolute).

I'm not saying that your machine is working correctly, and I'm not sure why you are having the problem you are having.  It just seems like an odd task you want to perform in a sudo command.

---

### Post by Thrasyllus on 2007-07-24
Thanks to all responders. I like the -i option because it sets up a condition familiar to me from older distributions, where one would log into a terminal as root and it would stay that way. 

To answer the last question, I resorted to sudo because I couldn't get into a directory as a non-owner. I have just switrched from Fedora to Ubuntu (after a motherboard meltdown) and have inherited dozens of directories needing to be cleaned up - some totally, others selectively. Maybe cd doesn't do much for you, but it lets me see what's in a directory and move files without writing lengthy paths. And doing sudo chmod on the target items so the ordinary user can then operate on them is not an attractive solution.

I guess I should have read the sudo man page more carefully. It seems a bit clunkily written, though.

---

### Post by Jason Quinn on 2008-04-14
The reason it is complaining is because the "cd" command is a shell built-in function, not an external command. Your system must lack an external cd executable. I've run into the same problem before. It's a nuisance. Apparently POSIX compliant systems should have a external cd command.

---

