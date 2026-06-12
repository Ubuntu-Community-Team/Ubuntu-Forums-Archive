---
title: "Known Bug: Firefox Starts offline"
date: 2008-06-16
forum: General Help
---

### Post by sheleztt on 2008-06-16
Firefox 3 starts offline. 
It's a problem in a network manager. NM doesn't recognize my internet connection via CDMA.
In Gnome i've solved the problem by enabling some kind of automatic network configuration, so system feels online.

But i cannot find solution in KDE. There is knetworkmanager, i tried to do the same thing i did in gnome-network-manager, but it didn't help.

So, what to do?

Kubuntu 8.04

Here is a bug report, but it seems like there is no solution for kde there. [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191889](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/191889)

---

### Post by sheleztt on 2008-06-16
help please :)

---

### Post by editrix on 2008-06-16
I don't have the problem, because I switched to FF2--which solved ALL my FF problems. However, one of the posts on Launchpad said this:



> Maybe I found solution to this problem:
[http://www.suseforums.net/index.php?showtopic=43981&pid=221062&mode=threaded&show=&st=&#entry221062](http://www.suseforums.net/index.php?showtopic=43981&pid=221062&mode=threaded&show=&st=&#entry221062)

"Knetworkmanager is still a little bit funky when it comes to accurately co-ordinating KDE's network online/offline status.
If you want, you could also disable the Network Status Daemon in Personal Settings -> KDE Components -> Service Manager. This will keep KDE from tracking network interface status, and hence all KDE apps will assume an active connection, rather than querying for online/offline status."


It sounds like a temporary solution to your problem.

---

### Post by sheleztt on 2008-06-17
> **editrix said:**
> I don't have the problem, because I switched to FF2--which solved ALL my FF problems. However, one of the posts on Launchpad said this:





It sounds like a temporary solution to your problem.
Thanks.
Switching to FF2 is not an option for me, becouse FF3 is much more faster on my system.
It's better to hit Alt+F>W every time it starts,then switching to slower FF2.

Disabling NetworkStatusDaemon is a partly solution. After disabling it, FF3 starts offline. But after switching it online, every other window of FF3 starts online.

---

### Post by peterroots on 2008-06-27
I had this problem with FF3 and Hardy and also kmail would not collect mail in Hardy or Fiesty using a usb speedtouch modem access via pon.
I solved this by editing /etc/network/interfaces so my file now looks like this:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface ppp0 inet ppp
provider tiscali

iface eth0 inet dhcp

iface eth1 inet dhcp

There is a file tiscali in my /etc/ppp/peers folder that is the one I used to access as pon tiscali.  This can now be done via networkmanager right-click dialup connections.
Originally I lacked the lines for eth0 (wired) and eth1 (wireless) as well as ppp0

---

### Post by savsav on 2008-06-27
I used to have that problem.

i uninstalled network manager , and that problem is now gone.

You should only uninstall Network Manager if you are - positively - sure you
do not need it.

---

