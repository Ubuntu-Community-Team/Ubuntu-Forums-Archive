---
title: "[SOLVED] Unable to log on as root"
date: 2008-06-21
forum: General Help
---

### Post by pedro1hayling on 2008-06-21
Just done a "clean" install of Ubuntu "Hardy" 8.04  all seemed well until I needed to log on as root to get the scanner working  -  find I cannot log on as root -  and I seem to remember during the install at no stage was I given this opportunity - seems strange to me, never had this b4.

Fast cure needed !


rgds P

---

### Post by ibutho on 2008-06-21
Hi.

Ubuntu by default works a bit differently than most distros. By default the root account is locked and you have to use sudo to gain root privileges or execute commands with root privileges. So prefix any commands with sudo or for graphical apps use ALT-F2 and enter "gksu command".

---

### Post by ad_267 on 2008-06-21
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by drs305 on 2008-06-21
If you already know about sudo but can't seem to use it, run the following. You should see your username and 'admin' listed among the output results.
```
groups
```

---

### Post by pedro1hayling on 2008-06-21
Hi

Thanks for the info /link   new to Ubuntu - have previously used Slackware suse and mepis,  Still lots to learn here... :-)

Best Rgds  P

---

### Post by aysiu on 2008-06-21
Probably the quickest way to get a root prompt is ```
sudo -i
```

---

### Post by pedro1hayling on 2008-06-21
Hi

Just to thank all for the replies - interesting !
Have now been in and installed the scanner driver, and edited snapscan.conf - I found it a bit awkward using this sudo/gksudu system but I guess it's not that often I need to go in and perform these tasks, still - scanner now works so problem solved

Cheers all  - P

---

