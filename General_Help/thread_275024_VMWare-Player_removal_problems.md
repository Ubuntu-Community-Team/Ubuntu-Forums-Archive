---
title: "VMWare-Player removal problems"
date: 2006-10-10
forum: General Help
---

### Post by montgoej on 2006-10-10
I installed VMWare player via Automatix2 and I got some kind of config error.  I ignored it then, because VMWare player seemed to work just fine anyways, but now, every time I try to do an apt-get install it'll give me something about vmware-player at the end, no matter what I install.  I did sudo dpkg- --configure -a like it said but I still get an error.

---

### Post by PriceChild on 2006-10-10
Could you paste this error? It could give us a lot more information :)

---

### Post by montgoej on 2006-10-10
The error reads as follows.  I just decided to do a simple apt-get install of firefox, even though it was already updated, the VMWare player shows up.

jordan@Jordan-Desktop:~$ sudo apt-get install firefox
Password:
Reading package lists... Done
Building dependency tree... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
cp: cannot stat `/usr/lib/vmware-player/share/locations.dist': No such file or directory
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
jordan@Jordan-Desktop:~$

I tried to uninstall and also purge the system of VMWare-player but it's still there

---

### Post by montgoej on 2006-10-10
Synaptic now says my software index is broken! I tried to fix it but it keeps wanting to download vmware-player!

---

### Post by montgoej on 2006-10-10
I still can't install anything and I keep getting an error.

---

### Post by EnderTheThird on 2006-10-17
I'm having the same problem.  :-/

---

### Post by Odisej on 2006-10-31
Me too. Help. It is anoying.

Odisej

---

### Post by Sir Frederic on 2006-11-20
Me too, someone help us, we're like poor little edgy efts that got stranded on a rock in the middle of a lava flow, Help! please help. Whimper whimper, yowl.

---

### Post by beerorkid on 2006-11-20
prob not gonna help you much, but I had it happen and got around it.

back in the day I had player installed (dapper) and wanted to install server, it kept getting mad that player was on there and refused.  I was never able to remove player, gave up and reinstalled.

Here at work I use server and wanted to install player, once again they do not play nicely.  After using automatix to install player I got the problem you are having now when doing an apt-get update/upgrade.  Neither server or player would work.  I went synaptic and removed any vmware thing I could find and reinstalled vmware server and now all is good, no player though.

---

