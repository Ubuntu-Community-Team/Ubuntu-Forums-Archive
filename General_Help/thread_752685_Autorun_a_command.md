---
title: "Autorun a command"
date: 2008-04-11
forum: General Help
---

### Post by Gauvenator on 2008-04-11
How can I make my computer run a command every time the X server starts?

I want to run:
nvidia-settings --load-config-only

Currently I have it run automatically when I login to Gnome, but I would like it to run when X starts so it will be in effect while I am in the login manager.

Edit:  The command must be run while X is running, otherwise it has no effect.

---

### Post by tvtech on 2008-04-11
edit the following from a terminal  this should start prior to X  

crack open a terminal and type 

[COLOR="Red"]username@localhost:~$[/COLOR][COLOR="Purple"]sudo nano /etc/rc.local[/COLOR] 

this is your boot script file you can add your start script here and it should open it up prior to login. I've only edited this file on the server so I'm not sure what it does with a display manager.  but it should do it prior to logging in I think.

---

### Post by Gauvenator on 2008-04-11
> **tvtech said:**
> edit the following from a terminal  this should start prior to X  

crack open a terminal and type 

[COLOR="Red"]username@localhost:~$[/COLOR][COLOR="Purple"]sudo nano /etc/rc.local[/COLOR] 

this is your boot script file you can add your start script here and it should open it up prior to login. I've only edited this file on the server so I'm not sure what it does with a display manager.  but it should do it prior to logging in I think.

I've tried that.  The problem is that the rc.local is loaded before X starts, so the command does nothing.

---

### Post by tvtech on 2008-04-11
have you tried to add a start scripts to the xorg.conf file?  not sure if that is possible?

---

