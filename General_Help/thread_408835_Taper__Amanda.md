---
title: "Taper / Amanda"
date: 2007-04-13
forum: General Help
---

### Post by EdLinq on 2007-04-13
I had some problems with another program.  In order to remove the left behind files I needed root access.  I did not know the root password.  I booted in the recovery mode which gave me root access.  From there I changed the root password and removed the offending files.  Now I am trying to load Taper or Amanda backup programs.  They appeared to load correctly but I can not find them in the menu lists.  Am I missing something with Taper or in changing the root password have I made loading new software a problem.  I used the passwd command that should have updated the shadow file.  Any thoughts?

---

### Post by amohanty on 2007-04-13
By default the root account is not directly accessible in ubuntu. Its supposed to be used via sudo. However if you change the root password in a root shell (which is what you did) you have now 'created a root account' (it was always there but you couldnt just do an su, had to use sudo. 

That does not mean you can no longer sudo.

When you say you are trying to load Taper or Amanda, are you trying to install them??
Are you using Synaptic?

Have you tried right clicking on the Applications button and selecting Edit Menus and see if its available there?

AM

---

### Post by EdLinq on 2007-04-13
I do not see it listed in the applications pull down menus nor via the edit function.  It appeards to have downloaded and installed but it did not put a link via the GUI for running.  Or, at least I can not find one.

---

### Post by EdLinq on 2007-04-13
Yes, I used Synaptic to download and install the packages.

---

### Post by amohanty on 2007-04-14
If you installed the amanda server, I think because they are servers/daemons you will not see them in the application menu. Thats usually reserved for GUI applications. To see something in the menus, look at the .desktop files in /usr/share/applications.

Can you try to run what you need from the terminal? I am assuming you are trying to setup backup options.

AM

---

### Post by EdLinq on 2007-04-14
I have not found any references to amanda in the usr/share/applications folder.  Some files exist in the /usr/scr/linix headers......... directory.  Maybe I am barking up the wrong tree.  I may need to learn more about these programs.  I am looking for a backup program.  Any other suggestions?

---

### Post by amohanty on 2007-04-15
Since you already have amanda:
[http://www.linuxjournal.com/article/7422](http://www.linuxjournal.com/article/7422)

Also keep in mind that not all programs that you install will show up in the application menu. Some are command line programs only and may not. Typically the approach is to tar gzip the file via a cron job and dump it to another hdd or network location.

[http://www.google.com/search?q=backup+using+tar+gzip](http://www.google.com/search?q=backup+using+tar+gzip)

HTH
AM

---

