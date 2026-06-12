---
title: "login problem and can't install software"
date: 2019-11-30
forum: General Help
---

### Post by sooperpotato8675309 on 2019-11-30
Hello.
I tried to log in on start up and got a black screen that lasted over a minute then was taken back to the log in screen and had to login again, which was successful. Afterwards the fan was running quite a bit more than it had previously. No error messages displayed. I see that login issues are common but did not see this specific version and wanted to see if it's normal system behavior. 

When I attempted to install hard info and sysinfo I got error messages. The one for Sysinfo from Ubuntu Software reads "Unable to install Sysinfo: E: Could not get lock /var/lib/dpkg/lock-fronted - open (11: Resource temporarily unavailable)"
The one for Hardinfo launched from the terminal read
"E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?"
Ubuntu 18.04.3 LTS
Mem: 5.5 Gib
Processor: Amd a9-9420 Radeon r5
Graphics: amd stoney
Gnome: 3.28.2
Os type: 64 bit
SanDisk ssd
Fresh install as of yesterday. Turned on UFW before connecting to internet

---

### Post by deadflowr on 2019-11-30
The message usually means the package manager utility, is already running somewhere.
Only one instance can be running at a time.
It might be Ubuntu has auto-updating enabling and it's installing the updates that have come since 18.04.3 has been released.

If that's the case waiting for the updating to finish usually fixes that.

Might also be Software Updater is open, check the dock (where the icons show on the desktop in that left pane),
and see if it's showing as an icon for it there.

---

