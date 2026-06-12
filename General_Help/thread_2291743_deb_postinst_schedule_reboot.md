---
title: "deb postinst schedule reboot"
date: 2015-08-22
forum: General Help
---

### Post by roland-logikalsolutions on 2015-08-22
This should be simple, but I cannot find trigger documentation or anything which will schedule a reboot immediately after package installation completes. I don't really want to issue a shutdown -r as the last line of the postinst because I'm not certain something like the software center would be allowed to complete its activities.

What is a good way to schedule a reboot from within the postinst file which will work no matter how the deb is installed? By that I mean it could be via software center, command line dpkg, or command line apt-get install.

Thanks

---

### Post by yetimon_64 on 2015-08-22
> This should be simple, but I cannot find trigger documentation or  anything which will schedule a reboot immediately after package  installation completes.
Why do you need to reboot ? Applications in linux use individual configuration files (stored either in /etc or in the hidden ~/.config directory in the users home folder) not a central registry like in Windows (which often needs a refresh by rebooting to work properly). 

The only updates or installations I've seen needing a reboot in Linux were kernel updates and one dbus update, normally a program works correctly immediately after installation in linux without rebooting.

Do you have a specific application that needs rebooting after installation or is this just a habit carried over from Windows practices ?

---

### Post by sandyd on 2015-08-22
Run
```

/usr/share/update-notifier/notify-reboot-required

```

You will get the standard "System reboot required" which shows up (depending on setup) in the following locations
1) Taskbar/Tray (GUI, dependent on Update manager)
2) MOTD when you login.

Note that this will require you to depend on the "update-notifier-common" package, which is installed by default on Ubuntu desktops (not sure about anything other than Kubuntu and Ubuntu, never used them). On Ubuntu servers, an ISO install will have update-notifier by default, but some OVZ/KVM/XEN/etc OS templates are missing this package. It seems to be missing most commonly in OVZ/XEN-PV VM's due to the shared kernel with the host (hence the lack of need for update-notifier which is normally used for notifying reboots after a kernel update)

---

### Post by roland-logikalsolutions on 2015-08-23
> **yetimon_64 said:**
> 
Do you have a specific application that needs rebooting after installation or is this just a habit carried over from Windows practices ?

Yes. It is a Kiosk type application which needs to restart the computer and auto-login to the kiosk account because that is what the users want.

---

### Post by roland-logikalsolutions on 2015-08-23
> **sandyd said:**
> Run
```

/usr/share/update-notifier/notify-reboot-required

```

You will get the standard "System reboot required" which shows up (depending on setup) in the following locations
1) Taskbar/Tray (GUI, dependent on Update manager)
2) MOTD when you login.



Thanks. The end users want an actual reboot though, not just a notification.

---

### Post by ian-weisser on 2015-08-23
The 'unattended-upgrades' package adds an apt config for rebooting.
I have not tried it.

See the 'unattended-upgrades' package, /etc/apt/apt.conf.d/50unattended-upgrades:
```
// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";

// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";

```

---

### Post by roland-logikalsolutions on 2015-08-23
> **ian-weisser said:**
> The 'unattended-upgrades' package adds an apt config for rebooting.
I have not tried it.

See the 'unattended-upgrades' package, /etc/apt/apt.conf.d/50unattended-upgrades:
```
// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";

// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";

```

Thanks! I will look into it after I get done once I finish identifying all of the 32-bit libraries my app needs to run on the various 64-bit flavors.

---

### Post by roland-logikalsolutions on 2015-08-31
> **ian-weisser said:**
> The 'unattended-upgrades' package adds an apt config for rebooting.
I have not tried it.

See the 'unattended-upgrades' package, /etc/apt/apt.conf.d/50unattended-upgrades:
```
// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";

// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";

```

Thanks again for mentioning this. Sadly it will be of little use. Much hacking (which would be difficult to undo during an un-install which might happen months, and many updates, later) would have to happen to the various config files. Adding insult to injury the package is not installed via apt-get. It is manually configured on a Web site and pulled down, then double clicked. I need to go digging in software-center to see if there isn't something I could put in the postinst to make it reboot.

---

