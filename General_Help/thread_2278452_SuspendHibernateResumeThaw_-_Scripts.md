---
title: "Suspend/Hibernate/Resume/Thaw - Scripts"
date: 2015-05-16
forum: General Help
---

### Post by kristoffer3 on 2015-05-16
[h=2]Suspend/Hibernate/Resume/Thaw - Scripts[/h][COLOR=#000000][INDENT]I need to run a script on a Suspend/Hibernate and on a Resume/Thaw. Now, I know the place to put the script is /etc/pm/sleep.d/ but this doesn't seem to work for a script requiring access to the network as the network is either already down or not up yet when it runs. Is there another place I need to put my script so it has access to the network before the network is shutdown on a suspend and after the network is up on a resume?

Basically, I just need to send out a curl command like:

echo -n "Resumed" | curl --data "Asus-Pundit=OFF" [http://192.168.0.1:8098/index.html](http://192.168.0.1:8098/index.html)
the command is working if i type it in terminal
I can see in the log (pm-suspend.log) that it is being executed but gives error "curl: (7) Couldn't connect to server" I guess because the network is already down
I have named the file "0000_suspend"

This works perfect in linux mint distro but when I do the same in Ubuntu it don't work. What is different in Mint  ???

I'm running ubuntu 14.04.[/INDENT]
[/COLOR]

---

### Post by kristoffer3 on 2015-05-17
I have tried different distros and this is the result

**Not working:**
Ubuntu 14.04
Lubuntury 14.04
Elementa os 0.3
Deepin linux
Linux Mint Xfce rebecca

**Working:**
Linux Mint Cinnamon rebecca
Linux Mint KDE rebecca
LXLE 14.04.2

Is there some smart person that know what can be the difference in the working distros. Maybe different network manager ? or power manager ?
I wans to use Ubuntu or Lubuntu.

---

### Post by kristoffer3 on 2015-05-18
Wow 150 views and not 1 reply.

---

