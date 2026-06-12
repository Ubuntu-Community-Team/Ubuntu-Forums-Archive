---
title: "Want to run swat 4 dedicated server"
date: 2007-05-13
forum: General Help
---

### Post by run3_kn1ght on 2007-05-13
Hi. I want to run a Swat 4 Dedicated Server on Ubuntu, but unfortunately there is no Linux executable for the game. There is a work around. However, since I'm a newbie to Linux I have no idea what the person is talking about:

[http://forums.vugames.com/thread.jspa?threadID=5019&tstart=0](http://forums.vugames.com/thread.jspa?threadID=5019&tstart=0)

(Scroll down to FritzE's post.)

> Until they get it right, here is how i managed to run the dedicated server on a Linux box running Fedora Core 4:

1 . Prerequisites

You need wine as well as an X server running on the machine. Since my machine doesnt normally run a GUI, i did a somewhat unconventional minimalistic install of X using the Xvfb server which renders into memory which serves as a dummy display. wine is pretty straight forward just yum install wine. I run the X server directly from /etc/inittab with TCP _enabled_ and _no_ access-control so port 6000 has to be blocked with iptables of course. The corresponding line in /etc/inittab looks like this:

vfb:3:respawn:/usr/X11R6/bin/Xvfb -ac -dpms -from 127.0.0.1 :0


2. Pitfalls


That stupid Swat4DedicatedServer.exe at some time during startup tries to bind to UDP port 0 which isn't allowed for ordinary users. I found no other way than running it as root (i know, dangerous but read on...)


3. Setup

Because of (2), i decided to establish a chroot-jail which is always a good idea and gives at least some protection. The attached init script builds the chroot environment on the fly by copying stuff from the real system into the chroot, mounts the swat4 diretory into that chroot and finally fires up the server using wine from within the - also attached - wrapper script. This has a nice side effect, that if the server eventually gets hacked and compromised you simply throw it away by stopping the server and on next startup it gets rebuild from scratch. The swat4 directory is simply a copy of an ordinary windows client-installation (some unneded stuff (Movies, .url and other crap) removed). So the Hierarchy is: swat4/Content/...

The file /etc/sysconfig/swat4, referenced by the script reads:

SWAT4ROOT=/home/swat4/.chroot

SWAT4USER=swat4

SWAT4DIR=/home/swat4/swat4

The first line defines the location where the chroot is created, the 3rd line specifies the location of the game copy from windows.

Another file, referenced in the script is /etc/swat4.screenrc. There, i usually put some screen-related settings (i run other game servers too). In this case, it simply can be empty since the screen-console is unusable because no input is possible in the console (except ctrl-c to stop the server).

The program nchroot is a somewhat extended version of the normal chroot program. It's special features are not needed here so you can replace it with the normal chroot call (man chroot(1))

The usual .wine dir, containing all settings is a copy from running wineprefixcreate on another machine. It is placed into the swat4 gamedir (in my case, the path is /home/swat4/swat4/.wine) Inside the dos_devices i remove the z: symlink and manually added a d: symlink pointing to ../..

Happy gaming

-FritzE 

He also includes 2 txt files.

Can someone please better explain how this works. What do I need to do to get my swat 4 dedicated server up and running?

Thanks a bunch!

---

### Post by run3_kn1ght on 2007-05-13
Bump. Please help!

---

