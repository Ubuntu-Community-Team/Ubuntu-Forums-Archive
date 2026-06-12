---
title: "Update Manager and Authentication"
date: 2013-12-17
forum: General Help
---

### Post by t0p on 2013-12-17
I just ran Update Manager and it updated a couple of packages - and it didn't require me to input my password for authentication.  I may be wrong, but I seem to remember that on previous occasions I had to input my password - which I think is sensible - for instance, if I want to run update in the terminal the command would be ```
 **sudo** apt-get update
``` wouldn't it?  Or am I misremembering?  After all, updating packages is a potential security vulnerability without authentication.  Yes?

---

### Post by claracc on 2013-12-17
No, for security updates it is not neccessary to introduce root password, only in certain cases as new kernels.
The reasen seems to be that is used an "aptdaemon" and not "apt".
See link: [http://askubuntu.com/questions/280228/how-can-update-manager-update-without-the-root-password](http://askubuntu.com/questions/280228/how-can-update-manager-update-without-the-root-password)

---

### Post by ian-weisser on 2013-12-17
> **t0p said:**
> I want to run update in the terminal the command would be ```
 **sudo** apt-get update
``` wouldn't it?  Or am I misremembering?

Your memory is accurate.

The Ubuntu Technical Board looked at the issue, and decided that install/remove should properly require the admin approval, but upgrading an already-installed (and already-admin-approved) package should not. If the admin wants to reject upgrades, the right way is to either disable the <release>-updates repository or to apt-pin a specific package version.

System Updater, as claracc pointed out, is not a simple apt script. Instead, it communicates with aptdaemon via dbus. Permissions for the unprivleged process to trigger package actions is granted by the AppArmor profile.

---

### Post by t0p on 2013-12-21
Thanks for explanation, all.

---

