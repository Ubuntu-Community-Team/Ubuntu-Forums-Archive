---
title: "Compiz Config Settings HELP"
date: 2008-05-21
forum: General Help
---

### Post by plutox989 on 2008-05-21
Hey guys,

I am completely new to linux (ubuntu) and have tried everything to solve this problem.

I recently installed emerald and compiz fusion. 

I open my CompizConfig settings manager and click the checkmark boxes by the effect I would like to choose, and it does not ever apply the effect when I click it.

What am I doing wrong?

---

### Post by Forlong on 2008-05-21
Did you run Compiz or ccsm being root lately?
Because then it might be a permission issue.

---

### Post by plutox989 on 2008-05-21
I simply went to systems>preferences>advanced desktop effects settings.

I'm not sure if that's what you're asking for?

---

### Post by plutox989 on 2008-05-21
Is there a difference b/w ccsm and compiz? I really do not understand what I am doing wrong. 

All I have done so far is installed compiz and it does not let me apply the settings. (same problem w/ emerald theme manager--I cannot apply the selected themes.)

---

### Post by Forlong on 2008-05-21
May I ask how you installed Compiz? And what version of Ubuntu are you currently using?

---

### Post by plutox989 on 2008-05-21
I installed it by going through 

software sources and through add/remove programs. (along w/ a variety of other different terminal commands i found onine until i finally got it to install)

I'm running ubuntu 8.04 (or whatever the newest version is. Hardy)

---

### Post by Forlong on 2008-05-22
OK, lets take several steps, just to make sure:

1. run ccsm, go to **Preferences** and make sure **Enable integration into desktop environment** is enabled.

2. While still In the Preferences, click on the **Plugin List** tab and make sure **Automatic Plugin sorting** is enabled

3. Close ccsm, open a terminal and run ```
sudo chown -R $USER:$USER $HOME
``` (just copy & paste the command as it is), this will make sure you are the owner of all the files in your home directory.
Afterwards run ```
chmod -R u+rwx $HOME
``` to make sure, you have the proper rights to those files.

4. Again in the terminal, run
```
gconftool-2 --recursive-unset -a /apps/compiz
``` this will reset all settings related to Compiz.

5. Finally run ```
ccsm
``` and change any setting you like. If anything fails, look for error messages in the terminal.

---

### Post by ashokraj on 2010-09-06
i am getting these errors :- 

GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Server ping error: IDL: omg.org/CORBA/COMM_FAILURE:1.0)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Server ping error: IDL: omg.org/CORBA/COMM_FAILURE:1.0)

---

