---
title: "How to execute script file on a CDROM"
date: 2007-08-14
forum: General Help
---

### Post by TimSNL on 2007-08-14
Hi

**Background:**
I am a software developer for a text interface program used in a terminal on linux.  We have begun using ubuntu 6.06 for our linux server.  When I send out program updates on CD, I want the user to put in the CD, the File Browser pops up (nice :)) and then the user just double-clicks on a script file and choose "Run in Terminal" which will install the program updates.

**Problem:**
Whenever I try to run a script file which is located in /media/cdrom it says
"bash: /media/cdrom/Setup.sh: Permission Denied"

File and path to file all have full read and execute permissions.
What is stopping this from executing?
Even using sudo still gives the same response.

I need to install using a script file because the same CD is also used on old RedHat 6.0 systems.  In this environment the program update script is run from the / direcorty of the linux server, but I thought ubuntu should be able to do better than that.

Thanks for your help.
Tim

---

### Post by pmg on 2007-08-14
When the CD is mounted, the **exec** option needs to be specified.  It doesn't appear to be included in the options in /etc/fstab on my feisty system.  Is adding it there a viable option?  How about overriding the options at mount time?

---

### Post by TimSNL on 2007-08-15
Thankyou - putting exec in fstab has fixed the problem.

**Another question:**
Some other linux servers we support are running kubuntu 5.10.  How do I run the script file from konqueror?
In gnome I just double-click the icon, select "run in terminal" and it works.
Kubuntu does not seem to want to run it from the icon.
Anyone know how to fix this?

---

