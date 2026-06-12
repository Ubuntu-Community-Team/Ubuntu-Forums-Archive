---
title: "Lubuntu 14.04 Vino-server Remote Desktop not accessible from boot at login screen"
date: 2015-02-08
forum: General Help
---

### Post by zikmen on 2015-02-08
Hi folks, 

I already tried to search the web a lot to solve my problem but the closest solution was this one but unfortunatly it refers to a file that does not seems to exists in Lubuntu 14.04.

[http://ubuntuforums.org/showthread.php?t=2073830](http://ubuntuforums.org/showthread.php?t=2073830)

i also readed these but didn't help.
[http://wiki.lxde.org/en/Autostart](http://wiki.lxde.org/en/Autostart)
[http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/](http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/)
[http://askubuntu.com/questions/159008/how-to-add-startup-applications-in-lubuntu](http://askubuntu.com/questions/159008/how-to-add-startup-applications-in-lubuntu)
[http://ubuntuforums.org/showthread.php?t=1868554](http://ubuntuforums.org/showthread.php?t=1868554)

The thing is thhat i can check the box for "desktop sharing" in the LXsessionConfiguration utility, that refers to the .desktop files located into /etc/xdg/autostart but it only start vino server until logged-in. it does not make the machine accessible after boot, at the login screen.

i cannot belive that i'm the only one using Lubuntu that needs the machine to be accessible from start at the logon screen.

Please tell us where to put the "/usr/lib/vino/vino-server" command.

---

### Post by zikmen on 2015-02-08
I'v readed some others treads but didn't helped yet.

[http://forum.lxde.org/viewtopic.php?f=8&t=36835&p=49987&hilit=autostart#p49987](http://forum.lxde.org/viewtopic.php?f=8&t=36835&p=49987&hilit=autostart#p49987)
[http://forum.lxde.org/viewtopic.php?f=3&t=36719&p=49597&hilit=autostart#p49597](http://forum.lxde.org/viewtopic.php?f=3&t=36719&p=49597&hilit=autostart#p49597)
[http://forum.lxde.org/viewtopic.php?f=8&t=31260&p=37278&hilit=autostart+boot#p37287](http://forum.lxde.org/viewtopic.php?f=8&t=31260&p=37278&hilit=autostart+boot#p37287)

It's important to be able to remote connect to the machine before anybody logged in on it since some machines are remote and nobody is there to type on the local keyboard. 
maby another solution could be to find how to manage "services" in lubuntu 14.

Try to help me, i am already helping myself the best i can browsing the web like crasy.

---

### Post by steeldriver on 2015-02-08
If you just need to remotely manage services, then it would be FAR easier and more secure imho to use a plain SSH session

---

### Post by zikmen on 2015-02-08
Some more reading, still not able to figure out how to start vino-server right after boot witout being logged-in.

i think the solution could be arount the "init" thing" help me up!

just want to start vino-server at the same time lightdm start.

[http://ubuntuforums.org/showthread.php?t=2218554](http://ubuntuforums.org/showthread.php?t=2218554)
[http://superuser.com/questions/511804/in-ubuntu-is-there-a-command-to-show-a-list-of-all-autostart-services](http://superuser.com/questions/511804/in-ubuntu-is-there-a-command-to-show-a-list-of-all-autostart-services)
[http://unix.stackexchange.com/questions/84252/how-to-start-a-service-automatically-when-ubuntu-starts](http://unix.stackexchange.com/questions/84252/how-to-start-a-service-automatically-when-ubuntu-starts)
[http://askubuntu.com/questions/335242/how-to-install-an-init-d-script-in-ubuntu](http://askubuntu.com/questions/335242/how-to-install-an-init-d-script-in-ubuntu)

This one is pretty interesting. i am still not sure to understand it totally.
[http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot](http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot)

---

### Post by zikmen on 2015-02-08
> **steeldriver said:**
> If you just need to remotely manage services, then it would be FAR easier and more secure imho to use a plain SSH session

i don't want to remote manage services, i want to remote desktop to a server that is stuck into a closet with no screen and keyboard. want a visual VNC connection.

---

### Post by zikmen on 2015-02-08
Maby a workaround, this post seems to explain how i could set the remote   machine with an autologin at boot, schedule 30 seconds later an   automatic session lock to secure the workstation and then restart the  vnc server to make it  available on the lock screen.

[https://bugs.launchpad.net/ubuntu/+source/light-locker/+bug/1287171](https://bugs.launchpad.net/ubuntu/+source/light-locker/+bug/1287171)

---

### Post by steeldriver on 2015-02-08
If it's in a closet with no screen or keyboard then imho vino (which is a ***desktop sharing*** type of server) just isn't the best tool for the job - better to log in via SSH and tunnel a standalone VNC session such as vnc4server or tightvncserver

---

