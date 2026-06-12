---
title: "How to proper uninstall software on Linux?"
date: 2016-03-15
forum: General Help
---

### Post by lakeshore2985 on 2016-03-15
I've been tinkering with this doubt since a very long time... how do you properly uninstall software on Linux?

I have tried sudo apt-get remove, remove --purge, remove --purge --autoremove but they all seem to keep files and directories intact (some software doesn't even get removed like Samba for example).

So am I doing something wrong or what?

---

### Post by oldos2er on 2016-03-15
```
sudo apt-get remove <package name>
``` or ```
sudo apt-get purge <package name>
``` *purge* will remove system configuration files; *remove* does not. Any config files in /home/user/ will not be deleted by apt-get.

All the details are in ```
man apt-get
```

---

### Post by lakeshore2985 on 2016-03-15
Thanks! I'd like to understand this further, the difference between  apt-get remove and apt-get purge... is there a correct order to do this? Also the difference between  uninstalling software on Linux and Windows, if any. Why is it so complicated? :/

> **oldos2er said:**
> Any config files in /home/user/ will not be deleted by apt-get.

Does it mean I have to manually delete any folders left in /home/user pertaining to the software after apt-get remove them?

---

### Post by sandyd on 2016-03-15
> **lakeshore2985 said:**
> Thanks! I'd like to understand this further, the difference between  apt-get remove and apt-get purge... is there a correct order to do this? Also the difference between  uninstalling software on Linux and Windows, if any. Why is it so complicated? :/



Does it mean I have to manually delete any folders left in /home/user pertaining to the software after apt-get remove them?

apt-get remove removes the application only. apt-get purge removes the application along with it's associated configuration files.

This is not much different than in Windows if you are using apt-get purge. For Linux, you are simply presented with more choices, in this case the choice to only remove the application and not the configuration files.

In Windows, application data pertaining to your user is stored somewhere in C:\Users\YourUser\AppData. The folder is hidden by default and you do not see it unless you manually browse to it. Most installers do not remove those folders after the application is installed. It is similar to Linux leaving the user-specific configuration files in the home folder

---

### Post by oldos2er on 2016-03-15
Yes, you have to manually delete anything leftover in /home/user/ if you want it gone. This goes back to the unix roots of Linux being a multiuser system, not having system package management touch a user's data. As you suggested, it's very different than the single user style developed by Microsoft for Windows (which I personally find to be complicated in comparison).

---

