---
title: "Problems with Kubuntu..launching programs etc"
date: 2006-07-28
forum: General Help
---

### Post by xenomorph99 on 2006-07-28
Hi,

Just moved over to KDE and a problem I used to get with live distros is happening...

1. When I launch programs, they occasionally take quite a long time to start up then just disappear (i.e. nothing appears on the desktop). 

2. When I launch kate via the terminal (then close it) , I see this:

> 
admin@admin-desktop:~$ sudo kate /etc/X11/xorg.conf
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
QObject::disconnect: Unexpected null parameter
~ScimInputContextPlugin()


3. I used to be able to (in Gnome) launch applications just by clicking on their icon. Now I get a dialog asking me what I want to open it with.

For information, I installed Kubuntu then rebooted. I then used EasyUbuntu to setup the usual stuff. I then changed my kernel to K7 and installed the nvidia drivers etc via the howto. I then rebooted. So, I don't know if this happened just after installing or is a result of easyubuntu/my messing about.

Regardless, is this sort of thing normal for KDE?

Ta,
Xeno

---

### Post by rocketman768 on 2006-07-28
No. Not normal for KDE.

---

### Post by xenomorph99 on 2006-07-28
Oh goody. Can someone suggest what might have gone wrong please?

Ta,
Xeno

PS: I had installed Kubuntu over Ubuntu by leaving the /home dir "in place"; I only formatted the / and swap partitions. Would this cause a problem?

---

### Post by gingermark on 2006-07-28
Use kdesu to launch a graphical program in KDE, not sudo. Using sudo with Kate can mess up your config files to the point where you may not be able to log in.

I have experienced the non-starting programs thing, although not in Dapper. In Breezy it used to happen, but didn't take too long, and they always ran the second time.

---

### Post by xenomorph99 on 2006-07-29
So, kdesu should be used as opposed to sudo for all instances?

---

