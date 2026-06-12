---
title: "apache server not working"
date: 2008-05-25
forum: General Help
---

### Post by AdiNX on 2008-05-25
Hello. I have a weird problem regarding the functionality of my LAMP server.
I have apachefriend's lampp package installed on my Kubuntu 8.04 system (on a Toshiba laptop). Everything works ok if the network cable is plugged in the laptop, but as soon as I unplug it, Konqueror shows me
```
An error occurred while loading http://localhost/xampp/splash.php:
Could not connect to host http://localhost/xampp/splash.php.
```
I figure this must be some sort of bug that prevents the browser to try to connect to any webpage, including localhost, if the system is not connected to a network.
I must add that I didn't have this problem until I switched from 7.10 to 8.04.
Please help me solve this problem.

---

### Post by AdiNX on 2008-05-27
I installed Firefox and tried connecting with it to localhost, and it worked.
So if anyone else can't connect to localhost while not being connected to a network, installing Firefox is the solution, as Konqueror has a bug that prevents any connections from happening while in Offline mode.

*Later Edit:*
I also found out how to fix Konqueror's problem. It seems there is a connection between Konqueror and KNetworkManager that doesn't allow Konqueror to connect to localhost if there is no Internet connection running.
The solution is pretty simple. Go to: K > System Settings > Advanced > Service Manager > Startup Services and disable Network Status Daemon.

---

