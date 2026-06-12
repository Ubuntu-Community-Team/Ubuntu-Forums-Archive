---
title: "Can't install Radeon driver"
date: 2012-11-06
forum: General Help
---

### Post by lukebolger on 2012-11-06
Hi guys, have installed ubuntu 12.10 x64 on my machine today, trying to get the driver for my radeon hd5670, and when i run the catalyst install i get the error 

"one or more tools for installation cannot be found on the system. install the required tools before installing the fglrx driver. Optionally, run the installer with --force option to install without the tools. Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended. see log for details."

log reads

Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-18-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

PLEASE HELP :)

---

### Post by CaptainLinux on 2012-11-06
> **lukebolger said:**
> Hi guys, have installed ubuntu 12.10 x64 on my machine today, trying to get the driver for my radeon hd5670, and when i run the catalyst install i get the error 

"one or more tools for installation cannot be found on the system. install the required tools before installing the fglrx driver. Optionally, run the installer with --force option to install without the tools. Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended. see log for details."

log reads

Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-18-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

PLEASE HELP :)

You need the headers for your kernel. Run the following to install them:

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by lukebolger on 2012-11-07
Thanks Captain Linux, 

But it didnt work..

luke@luke-GA-880GM-UD2H:~$ sudo apt-get install linux-headers-$(uname -r)
[sudo] password for luke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.5.0-18-generic
E: Couldn't find any package by regex 'linux-headers-3.5.0-18-generic'

---

### Post by timgood on 2012-11-07
Try ```
sudo apt-get install linux-headers-generic
```

Hope this helps.

---

### Post by Senic on 2012-11-08
Thanks [timgood]("http://ubuntuforums.org/member.php?u=186361") I had the same problem and this fixed it for me! :)

---

