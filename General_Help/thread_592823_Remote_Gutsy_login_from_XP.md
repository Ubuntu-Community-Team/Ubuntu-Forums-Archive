---
title: "Remote Gutsy login from XP"
date: 2007-10-26
forum: General Help
---

### Post by FighterOfTheNightMan on 2007-10-26
Hey,

I've tried searching for a solution to this tha is with Gutsy Gibbon, but I cannot find it.  I want to be able to log in from an XP machine to my machine at home.  Any help is greatly appreciated.

Regards,

Brandon

---

### Post by taurus on 2007-10-26
You need to install ssh server on your Ubuntu before you can log in from another machine.  The package you need is openssh-server.  Then, make sure you open port 22 for incoming traffic if your Ubuntu is behind a router or a firewall.

---

### Post by FighterOfTheNightMan on 2007-10-26
Do you have a tutorial I can go by?  I want to be able to view my desktop and use that, I don't want to do it from a shell.  Still not that experienced at the command line, but I'm getting there.

Regards,

Brandon

---

### Post by isecore on 2007-10-26
> **FighterOfTheNightMan said:**
> Do you have a tutorial I can go by?  I want to be able to view my desktop and use that, I don't want to do it from a shell.  Still not that experienced at the command line, but I'm getting there.

Regards,

Brandon

Enable the "Remote Desktop" in System - Preferences. Make sure you set a secure password, and uncheck that you have to allow anyone access.

Provided you have a direct connection to the net you can then use any VNC-client to connect to your IP-adress at home. You could also setup a dynamic hostname to ease this, but I'm too lazy to go into detail on that now ;)

This method allows you to connect to your desktop just as if you were at home.

---

### Post by bodhi.zazen on 2007-10-26
[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

---

### Post by Vaan on 2007-10-26
This is the "real" way to have remote multi-session logins from XP to your Ubuntu host located inside a LAN.


First on your Ubuntu machine goto:

[I]System > Administration > Login Window
[/I]
Under the **General** tab make certain the **Default session:** is set to 
**GNOME**. Afterwards click on the **Remote** tab and set the **Style:** to  **Same as Local**.


Now on your XP machine download and install an application called [Xming]("http://www.straightrunning.com/XmingNotes/") which is basically an X Window server for Windows. It'll allow you to remotely login to your Ubuntu machine.

After you have it installed start it up and connect to your Ubuntu host machine (192.168.0.x) which should be located inside your LAN. If you get any black screens or the Ubuntu login window doesn't load, you may have to temporarily disable your firewall(s).

---

