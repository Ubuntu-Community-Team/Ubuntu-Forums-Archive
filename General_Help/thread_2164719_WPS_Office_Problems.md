---
title: "WPS Office Problems?"
date: 2013-08-01
forum: General Help
---

### Post by Sly14Cat on 2013-08-01
Hello,
I have a fresh installation of Xubuntu from last night and I've decided to try out WPS Office. For some reason, it won't start. Has anyone else had the same problem?

---

### Post by GwL3eNC on 2013-08-01
Hallo,

I assume that you have downloaded the deb file on kingsoft homepage and installed it. How do you try to
start the application now? Over an icon from Menu? Because if so, you cant see any error messages. If you try
starting the application from terminal you evtl. see some messages explaining why it wont start.

---

### Post by Sly14Cat on 2013-08-01
How would I go about starting it from the terminal?

---

### Post by GwL3eNC on 2013-08-01
You need to know the name of the startup file. I dont know it, but evtl it begins with wps. I would open a terminal and type
wps and use a fast double press on tab key to use autocomplete. Press enter and hope it works.

Or if you can view the application link in a text editor, somewhere you can find the application name.

---

### Post by Sly14Cat on 2013-08-01
Alright so, 
I've attemped to open the "presentation" aspect of the program. The menu says that the command to open it is "/usr/bin/wpp %f"... 
[B]
AHA I've found the problem.[/B] If you are using a x64 bit system as I am, you need to install the 32-Bit architecture (I'm used to Windows doing it for me). To do so do these commands:
$ sudo apt-get install ia32-libs
$ sudo dpkg --add-architecture i386[B]
Then you must install using this command
[/B]# dpkg -i --force-architecture packagename.deb
[B]Once it is installed, use 
[/B]$ cd /opt/kingsoft/wps-office/office6/2052
**and**
# sudo rm qt.qm wps.qm wpp.qm et.qm
[B]To make most features english. I hope this helps others in the future.
[/B]
[I]Thank you for your time,
Sly14Cat[/I]

---

