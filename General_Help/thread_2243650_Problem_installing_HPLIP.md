---
title: "Problem installing HPLIP"
date: 2014-09-10
forum: General Help
---

### Post by daniell59 on 2014-09-10
Ubuntu 14.04 32

I don't know how to proceed.

Thanks in advance.

---

### Post by rbmorse on 2014-09-10
Is the file marked as executable?  Find the file in Nautilus, right click on it, click on "properties", click on permissions.  There should be a checkmark in the box "Allow executing file as a program"

---

### Post by buzzingrobot on 2014-09-10
Hplip is an HP script that, when executed in a terminal, will prompt you with several questions, download and install any needed drivers from HP, and setup the printer. 

You might find it easier to install and use 'hplip-gui' (in the repos) which does the same thing via a GUI. 

In both cases, you will need to know how your printer is connected, etc.

After completing the install with the HP tool, I've found it's a good idea to run through Ubuntu's printer config, too.

---

### Post by daniell59 on 2014-09-10
Someone on the HP Linux Imaging and Printing site helped me. The following commands in the terminal did it.

=> Reconfigure print queue using below commands.
=> hp-setup -r (remove all print queues)

=> sudo hp-plugin (This will download right plugin)

=> hp-setup

---

