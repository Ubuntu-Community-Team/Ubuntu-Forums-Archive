---
title: "NVidia Users: GUI does not load after kernel update"
date: 2006-09-14
forum: General Help
---

### Post by jdong on 2006-09-14
Attention Nvidia Graphics Card Users:


There was a problem with the recent kernel update that breaks the nvidia 3D graphics drivers. If you've recently updated your kernel and your X server does not start, please read this information.


**Am I affected?**
If you see a blue screen with an error about starting the X server, then you are affected. If you updated your system on September the 14th, between 14:00 and 20:00 UTC, you should check for and apply all updates before rebooting:

 1. Open up System->Administration->Update Manager
 2. Press **Check**
 3. Ensure that there are no new updates. Install them if they show up.

**Fixing the problem**

Updated drivers have been uploaded to the repositories and should be available within minutes of this posting.

 1. If you are at a blue screen, press ALT+F1 to get a login prompt.
 2. Log in with your username/password.
 3. Type **sudo apt-get update**
 4. Type **sudo apt-get upgrade**
 5. Answer yes when it prompts if you want to update.
 6. You should see "linux-restricted-modules" as some of the packages being updated. If you do not, repeat steps 3-5 every few minutes until you do.
 7. Once you have successfully retrieved and updated these packages via this procedure, type in **sudo reboot** to restart your system.


**What Happened**?

An error was made during the preparation of the kernel update package for USN-346-1. Once this was identified, the faulty packages were immediately disabled from the Ubuntu download servers. USN-346-2 was issued a few hours later to correct this error.

[http://www.ubuntu.com/usn/usn-346-1](http://www.ubuntu.com/usn/usn-346-1)
[http://www.ubuntu.com/usn/usn-346-2](http://www.ubuntu.com/usn/usn-346-2)


For a more in-depth technical description of what went wrong, please see the [Launchpad Bug and discussion]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/60433") regarding this issue.


We apologize for any inconvenience this may have caused.


ADDENDUM: There appears to be at least one other regression introduced by this kernel update. These are currently being investigated and fixes will be released to resolve these issues as they become available.

If you have a Marvell/Yukon network card and it no longer functions, please see [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/60271](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/60271) for the status of that fix.

If you experience sound problems or a freeze at login, the fix has already been written for Dapper, and will be uploaded soon. See [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/52649](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/52649) for more information.

---

