---
title: "unable to run a script or terminal command on startup , ubuntu 18:04"
date: 2018-09-26
forum: General Help
---

### Post by arsen2 on 2018-09-26
Hello  ,
I am new to the forum, so please forgive me if this wrong way to ask the question.

I am trying to get nordvpn auto connect on start up. 

For this I did the following :

sudo gedit /etc/rc.local

and added this line in the file

#!/bin/sh

nordvpn connect

so this was supposedly way to start it at the boot, but it did not work.

Please help get this solved, thank you !

update: the file itself is executable

---

### Post by ajgreeny on 2018-09-26
A few points worth making.

Firstly, never use sudo for a GUI application such as gedit, use **sudo nano /etc/rc.local** instead, or if you must use a GUI application use **sudo -H gedit /etc/rc.local**

See Root-Sudo in my signature below for info about this.

In your rc.local file you do not need the #!/bin/bash line; just add the **nordvpn connect** line alone to see if that works for you.
There may even be better ways to get your vpn connection working for you but I'm afraid I am not the right person to give that advice so wait for others to appear.

---

### Post by TheFu on 2018-09-26
There isn't much of any environment during startup and for system stuff.   The full path to the program you want to run is necessary. Find that with **which nordvpn**.  That should return the correct answer. If it doesn't, find it.

If nordvpn has a GUI, none of this will work.  GUI programs cannot be run prior to a login session being created.

If you use **sudoedit /etc/rc.local**, it will work with any editor correctly, even GUI ones, if those work on it.  If you want a different editor, just add **export EDITOR=gedit** to your ~/.bashrc file.  Any editor will work fine.

In 18.04, I think rc.local is disabled. Others have tried to enable it, but it doesn't seem to work.  systemd has a new way (relatively), to enable start and stop for stuff like this. There are examples on the system under /etc/systemd/ ... find one that seems simple and work from that.

I don't use nordvpn, but I do use others based on openvpn.  The start/stop for my setup isn't sensitive to the pwd/cwd, but my config files are setup with full, completely, absolute paths for any external references.

---

### Post by arsen2 on 2018-09-28
Hi thanks for reply, I did tried your solution it did not work.

---

### Post by arsen2 on 2018-09-28
> **TheFu said:**
> There isn't much of any environment during startup and for system stuff.   The full path to the program you want to run is necessary. Find that with **which nordvpn**.  That should return the correct answer. If it doesn't, find it.

If nordvpn has a GUI, none of this will work.  GUI programs cannot be run prior to a login session being created.

If you use **sudoedit /etc/rc.local**, it will work with any editor correctly, even GUI ones, if those work on it.  If you want a different editor, just add **export EDITOR=gedit** to your ~/.bashrc file.  Any editor will work fine.

In 18.04, I think rc.local is disabled. Others have tried to enable it, but it doesn't seem to work.  systemd has a new way (relatively), to enable start and stop for stuff like this. There are examples on the system under /etc/systemd/ ... find one that seems simple and work from that.

I don't use nordvpn, but I do use others based on openvpn.  The start/stop for my setup isn't sensitive to the pwd/cwd, but my config files are setup with full, completely, absolute paths for any external references.



Thanks for the reply, but I am struggling to do the same with /etc/systemd, do you mean I need to copy the config over there ? 
Sorry for noob questions.

---

### Post by arsen2 on 2018-09-30
Update: 
Got it sorted out, by creating simple script, and adding to start up.
Other options did not work for me.

thanks

---

