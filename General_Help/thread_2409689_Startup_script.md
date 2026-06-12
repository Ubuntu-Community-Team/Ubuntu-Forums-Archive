---
title: "Startup script"
date: 2019-01-05
forum: General Help
---

### Post by yegnal on 2019-01-05
I want to run a simple shell command at startup:

echo enabled > /sys/bus/usb/devices/3-8/power/wakeup

It would have to run as root user.  I tried writing it to /etc/rc.local but that didn't do anything. Then read that every entry into rc.local needs to end with exit 0 so I did that but when I booted my desktop was changed like I created a new user.  After I erased the rc.local entry and re-booted things went back to normal.

I tried creating a shell script, granting it 755 permission and x permission and placed it into /etc/init.d   That didn't work, 

This simple shell command allows my machine to wake from suspend via my usb mouse/keyboard.  If I open a shell, logon as su and run that command it works great but every re-boot of the machine resets the condition.

I'm sure it's easy enough, but most of what I find seems to assume a certain understanding of Linux whereas I only have the most elementary knowledge.  I can follow specific steps easily enough.. but rudimentary details would be important for me.

---

### Post by coffeecat on 2019-01-05
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by apmcd47 on 2019-01-05
Assuming the file is called wake_on_mouse you could try this:

```
ln -s /etc/init.d/wake_on_mouse /etc/rc3.d.S99wake_on_mouse
```
Basically the init.d directory is only a repository for these scripts. As Linux starts up and shuts down it goes through different run levels. 0 is shutdown level and 3 is user mode. As it enters a run level it runs any files it finds in the appropriate rc?.d directory for the run level and runs any scripts starting with S (with the argument start) in that directory in alpha-numerical order. When it leaves that level it runs any files starting with K (with argument stop).

At least it used to. Ubuntu currently uses systemctl to start and stop services, but I think the init scripts are still used for services which are not systemctl-aware.

If this fails you could add the following line to root's crontab:
```
@reboot echo enabled > /sys/bus/usb/devices/3-8/power/wakeup 
```

This should run the command from cron every time the system is rebooted.

Andrew

---

