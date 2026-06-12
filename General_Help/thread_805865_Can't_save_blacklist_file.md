---
title: "Can't save /blacklist file"
date: 2008-05-24
forum: General Help
---

### Post by paperpig on 2008-05-24
Absolute Noob
I'm installing Ubuntu 8.04 on an asus eeepc 900. I'm following [the instructions]("https://help.ubuntu.com/community/EeePC/Fixes") for allowing wireless access.
The madwifi fix didn't work so I'm following the second Ndiswrapper work around.
I need to edit /etc/modprobe.d/blacklist which I have done but i can't save it. I get the message 'You do not have the necessary permissions to save the file.' I'm using Edit to edit he file. 
Any help would be gratefully accepted :-)
PP

---

### Post by sisco311 on 2008-05-24
You need to run the editor as super-user.
Press Alt+F2 and type:
```
gksu gedit /etc/modprobe.d/blacklist
```
and press the *Run* button. 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Nepherte on 2008-05-24
You have to open the file with sudo privileges by placing sudo in front of the command:
```
sudo gedit /etc/modprobe.d/blacklis
```
(command should be typed in a terminal)

---

