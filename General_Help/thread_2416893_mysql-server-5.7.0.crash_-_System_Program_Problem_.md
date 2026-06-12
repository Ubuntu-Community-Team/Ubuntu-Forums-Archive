---
title: "mysql-server-5.7.0.crash - System Program Problem Detected"
date: 2019-04-17
forum: General Help
---

### Post by BravoDelta65 on 2019-04-17
Ubuntu 18.04

I'm trying to return to using Ubuntu as my main Desktop OS, as Win7 is being sent out to pasture.
I'm in the process of trying to set up a LAMP dev environment, so I can develop the odd website here and there.
I've tried following tutorials to install using Tasksel, but ran into problems when it came to installing and configuring Mysql.
Not having any success, I decided to uninstall everything and start again. Following other tutorials I removed everything. I suspect this is where my problem comes from.

When booting up I see a 'System Program Problem Detected' error come up on screen. The first time I clicked the report button, but this didn't make the message go away.

On search for a solution I have found out to look in /var/crash. There is a file there: mysql-server-5.7.0.crash

I have since sought a different solution for my LAMP needs - XAMPP, but this of course this hasn't solved the cause of the problem producing the crash report.


I don't know how to proceed. I have since tried to install a separate mysql-server, assuming there is one needed by Ubuntu OS? but I don't know what to do after installing the server to get it working as Ubuntu expects.....

or should I just re-install Ubuntu 18.04?


Thanks for any help

---

### Post by joegry on 2019-04-20
You could try reinstalling Ubuntu to start clean.  How did you try to remove mysql-server?  You could try sudo apt-get remove mysql-server-5.7 to see if it will remove completely.  You may want to check out the man page for apt-get as there are other command flags that can help you clean up an installation if it fails to remove completely.  If you do get it to remove completely using apt-get you can just reinstall it using sudo apt-get install mysql-server-5.7

---

