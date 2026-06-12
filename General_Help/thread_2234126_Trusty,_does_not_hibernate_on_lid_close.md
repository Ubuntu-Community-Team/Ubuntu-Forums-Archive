---
title: "Trusty, does not hibernate on lid close"
date: 2014-07-12
forum: General Help
---

### Post by fedebaka2 on 2014-07-12
I have an Acer aspire 5551 notebook and installed Xubuntu 14.04 fresh. I enabled hibernation by editing /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla and sudo pm-hibernate works (it acts up but I'll research it or post another thread). I set the computer to hibernate on lid close, both for AC and battery, in energy settings.
When I close the lid, the computer seems to suspend, not hibernate. I t doesnt fully turn off and it wakes up to the unlock screen dialog upon pressing any key.

I know there are some threads for this in older versions, but I'm not sure any of the solutions apply to me:

[this thread]("http://ubuntuforums.org/showthread.php?t=2161901") says to edit both /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla AND /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla , but the latter doesn't exist in my system.

[This thread]("http://askubuntu.com/questions/291903/ubuntu-not-is-hibernating-when-lid-is-closed") says to use cinnamon-settings (?? doesn't apply to xubuntu trusty, right?) and edit /etc/acpi/lid.sh , but this file doesn't exist in my system either.

Any help?

Thanks!

---

### Post by sandyd on 2014-07-12
Try running the following.
```

sudo sed -i s/#HandleLidSwitch=suspend/HandleLidSwitch=hibernate/ /etc/systemd/logind.conf
sudo restart systemd-logind
```

---

### Post by ajgreeny on 2014-07-12
I followed all the info in [http://ubuntuforums.org/showthread.php?t=2219403](http://ubuntuforums.org/showthread.php?t=2219403) and my old netbook running Xubuntu 14.04 now hibernates just like it did with 12.04 when I close the lid, essential for that machine which has short battery life.

---

### Post by fedebaka2 on 2014-07-12
Thanks for your responses!

@sandyd, you were right in that /etc/systemd/logind.conf said HandleLidSwitch=suspend. I changed it to hibernate. No change, it keeps suspending on lid close.

@ajgreeny, I think that thread is about enabling hibernation, not about hibernating on lid close. I actually had already edited /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla the way it says in the thread and hibernation was enabled. The thread mentions /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla and /var/lib/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla instead, which don't exist in my system. I even created them anyway adding the lines, and no effect. It keeps suspending on lid close.

Any other ideas anyone?

---

### Post by Toz on 2014-07-12
> When I close the lid, the computer seems to suspend, not hibernate. I t doesnt fully turn off and it wakes up to the unlock screen dialog upon pressing any key.
What does /var/log/pm-suspend.log say? 



Also, can you post back the results of:
```
xfce4-power-manager --dump
```
...and:
```
cat /var/log/syslog | grep PM:
```

---

### Post by fedebaka2 on 2014-07-12
Sillly me! @Sandyd's solution is just right! I had to uncomment (erase the #) the line for it to work! So to summarize:

To enable hibernation:
edit (as root) /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla (ex. sudo mousepad /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla)
In the part that says:
```
[Disable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=no

[Disable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=no
```
replace both ResultActive=no for ResultActive=yes

To enable hibernation on lid close:
edit (as root) /etc/systemd/logind.conf (ex. sudo mousepad /etc/systemd/logind.conf)
change the line "#HandleLidSwitch=suspend" for "HandleLidSwitch=hibernate"
restart, or sudo restart systemd-logind

@toz if you still need the logs for research or something, let me know.

Thanks all!

---

