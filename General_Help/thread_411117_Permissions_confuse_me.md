---
title: "Permissions confuse me"
date: 2007-04-16
forum: General Help
---

### Post by Afkpuz on 2007-04-16
I recently installed the Java Runtime environment and had saved the download to my desktop.  I installed it and now there is a new folder on my desktop called jre.6.0_01.  I can't do anything with this file becuase I don't have the permission to do squat. It says I'm not the owner..but I really am! No one else uses the computer.  So how do I move or delete this file? Do I still need it on my desktop for Java to work? Help!

---

### Post by crosintoski on 2007-04-16
You need to be root to delete the folder.  Open a terminal and type ```
su 
``` and press enter.  Then type the root password.  If the root password has not been set, in the file menu, go to system > administration > users and groups.  Select the root user and select properties.  Change the password.  Now back to the terminal.  Type ```
su
``` and press enter.  Enter the root password.  Change to the directory where your file is.  Probably this:```
 cd Desktop
```.  type ```
rm <name of the folder you want to delete>
```.  Should work

---

### Post by namityadav on 2007-04-16
I think we should encourage users to use "sudo" instead.

Assuming you want to remove a file called AFILE .. for which you don't have permissions. Run the command with "sudo " as prefix. Thus your command becomes: "~$sudo rm AFILE". This will ask for your password (Your password, not the root password). Enter the password, and the file will be removed. If you want to change the owner of the file to yourself instead, then use: "~$sudo chown yourid AFILE", where yourid is the login-id of yours.

This is obviously assuming that you are in the sudoers list. Since you are the only user of the system. I am almost positive that you are.

---

### Post by energiya on 2007-04-16
**Afkpuz**
> 
cd ~/Desktop
sudo rm -r jre.6.0_01

This is not nrmally needed for jre to run asfter installing. I think.

**crosintoski**, rm <dir> will fail. You have to use
> 
rm -r <dir_name>

To remove a folder and all its contents.

> **namityadav said:**
> I think we should encourage users to use "sudo" instead.

Never did liked using "sudo", I also prefer "su" and "su -c"

---

### Post by crosintoski on 2007-04-16
Sorry forgot -r

---

### Post by Afkpuz on 2007-04-16
That did it. Thanks guys!

---

