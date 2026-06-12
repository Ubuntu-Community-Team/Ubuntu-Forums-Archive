---
title: "Privileges, Root, and USB Not Working"
date: 2007-01-14
forum: General Help
---

### Post by Chris361 on 2007-01-14
First off, I just installed Ubuntu 6.10 yesterday on my Compaq Presario R3440CA. The wireless, being the Broadcom BCM chipset, didn't work at first but now works. Now I am starting to realize that I have more problems then I previously knew about.

**USB Mouse Does Not Work**
This is probably one of the more frustrating problems, right from the first time I booted up the laptop to the live cd, the USB Logitech Optical mouse has not worked. Changing USB ports has no effect on the mouse. On Windows, the mouse works fine, so it isn't a problem with the mouse.

**WPA And WEP Do Not Work**
The wireless works only on a non-encrypted network, and I am not going to keep the network open, and since I go to college, the network there is also encrypted, and the SSID is not broadcasted.

**Permissions are Driving me Nuts and the Root Login Does Not Work**
I was trying to install something through the terminal, and the next step required me to edit the etc/apt/sources.list file in the filesystem. When I open the text editor, I can load up the file but it is in Read Only mode. Trying to change the permissions does not work either, because I am not root. So I enabled the ability for the Root user to login through the main login screen. The keyboard and mouse didn't work. WTF. What do I do now?

Anyone that knows how to fix these problems please reply, I like linux, although I am an advanced Windows user (I have worked as a PC repair technician), I think that is my reason for wanting to run Linux even more.

Thanks guys,

Chris Bowman

---

### Post by Chris361 on 2007-01-14
So I have figured out half of the Privileges and Root problem.

The command to open and edit the file is:

> sudo gedit etc/apt/source.list

However, the rout login keyboard and mouse problem is still no resolved.

---

### Post by jd65pl on 2007-01-14
There should/is no need for you to login as root you can do it all via 'sudo' but if you must log in as root do this

*SYSTEM>ADMIN>LOGIN>SECURITY>ENABLE ADMIN LOGIN*

---

### Post by dcstar on 2007-01-14
> **Chris361 said:**
> First off, I just installed Ubuntu 6.10 yesterday on my Compaq Presario R3440CA. The wireless, being the Broadcom BCM chipset, didn't work at first but now works. Now I am starting to realize that I have more problems then I previously knew about.

**USB Mouse Does Not Work**
This is probably one of the more frustrating problems, right from the first time I booted up the laptop to the live cd, the USB Logitech Optical mouse has not worked. Changing USB ports has no effect on the mouse. On Windows, the mouse works fine, so it isn't a problem with the mouse.
........
CTRL-ALT-F1 to get to a terminal login, login as normal and then:
```
sudo dpkg-reconfigure xserver-xorg
```
See if it auto-detects the mouse, if not then try and select the correct one.

ALT-F7 to go back to the X system, then CTRL-ALT-BACKSPACE to restart the X server and test out the new settings.

Repeat as necessary for trying different things........

---

