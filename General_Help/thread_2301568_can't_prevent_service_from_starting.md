---
title: "can't prevent service from starting"
date: 2015-11-03
forum: General Help
---

### Post by schplurtz on 2015-11-03
Hi.

I just installed a new Ubuntu 14.04.3 amd64 Desktop with no customization
to make tests.

The initial problem is that all printing dialogs are filled with automagically
discovered network printers. After reading and trying some of the solutions
mentionned in
[http://askubuntu.com/questions/507099/why-do-weird-printers-show-up-in-the-ubuntu-printing-dialog](http://askubuntu.com/questions/507099/why-do-weird-printers-show-up-in-the-ubuntu-printing-dialog)
and [http://askubuntu.com/questions/345083/how-do-i-disable-automatic-remote-printer-installation](http://askubuntu.com/questions/345083/how-do-i-disable-automatic-remote-printer-installation),
the only real solution seems to be : stop avahi daemon.

Unfortunately, I can't find a way to prevent avahi-daemon to start at boot.
Here is what I did :
```
sudo update-rc.d avahi-daemon stop 80 0 1 2 3 4 5 6 S .
```
When I reboot, avahi-daemon is still there. Since /etc/init.d/cups and
/etc/init.d/cups-browsed service both have a "Should-Start: avahi-daemon" line,
I also disabled (temporarily) cups and cups-browsed.
```
sudo update-rc.d cups stop 80 0 1 2 3 4 5 6 S .
sudo update-rc.d cups-browsed stop 80 0 1 2 3 4 5 6 S .
```
After a reboot, avahi-daemon and cups are still there, (and the printing dialogs
still filled with discovered network printers)

Something launches avahi-daemon at boot, but What ?
Is there a way to disable avahi-daemon ?

Schplurtz.
```
 cd /etc && ls -l rc*d/*avahi* rc*.d/*cups*
lrwxrwxrwx 1 root root 22 nov.   3 09:43 rc0.d/K80avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root 14 nov.   3 09:48 rc0.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 22 nov.   3 09:48 rc0.d/K80cups-browsed -> ../init.d/cups-browsed
lrwxrwxrwx 1 root root 22 nov.   3 09:43 rc1.d/K80avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root 14 nov.   3 09:48 rc1.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 22 nov.   3 09:48 rc1.d/K80cups-browsed -> ../init.d/cups-browsed
lrwxrwxrwx 1 root root 22 nov.   3 09:43 rc2.d/K80avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root 14 nov.   3 09:48 rc2.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 22 nov.   3 09:48 rc2.d/K80cups-browsed -> ../init.d/cups-browsed
lrwxrwxrwx 1 root root 22 nov.   3 09:43 rc3.d/K80avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root 14 nov.   3 09:48 rc3.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 22 nov.   3 09:48 rc3.d/K80cups-browsed -> ../init.d/cups-browsed
lrwxrwxrwx 1 root root 22 nov.   3 09:43 rc4.d/K80avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root 14 nov.   3 09:48 rc4.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 22 nov.   3 09:48 rc4.d/K80cups-browsed -> ../init.d/cups-browsed
lrwxrwxrwx 1 root root 22 nov.   3 09:43 rc5.d/K80avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root 14 nov.   3 09:48 rc5.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 22 nov.   3 09:48 rc5.d/K80cups-browsed -> ../init.d/cups-browsed
lrwxrwxrwx 1 root root 22 nov.   3 09:43 rc6.d/K80avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root 14 nov.   3 09:48 rc6.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 22 nov.   3 09:48 rc6.d/K80cups-browsed -> ../init.d/cups-browsed
lrwxrwxrwx 1 root root 22 nov.   3 09:43 rcS.d/K80avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root 14 nov.   3 09:48 rcS.d/K80cups -> ../init.d/cups
lrwxrwxrwx 1 root root 22 nov.   3 09:48 rcS.d/K80cups-browsed -> ../init.d/cups-browsed

ps -ef | grep -e avahi -e cups
avahi  807     1  0 10:31 ?        00:00:00 avahi-daemon: running [226xldo232.local]
avahi  861   807  0 10:31 ?        00:00:00 avahi-daemon: chroot helper
root  1646     1  0 10:32 ?        00:00:00 /usr/sbin/cupsd -f
lp    1649  1646  0 10:32 ?        00:00:00 /usr/lib/cups/notifier/dbus dbus://
lp    1650  1646  0 10:32 ?        00:00:00 /usr/lib/cups/notifier/dbus dbus://
lp    1651  1646  0 10:32 ?        00:00:00 /usr/lib/cups/notifier/dbus dbus:// 
```

---

### Post by Lars Noodén on 2015-11-03
avahi-daemon seems to be run by [Upstart](http://upstart.ubuntu.com/cookbook/) instead.  So you can turn it off by adding the file "avahi-daemon.override"

```

sudo sh -c ' echo "manual" >> /etc/init/avahi-daemon.override '

```

---

### Post by schplurtz on 2015-11-03
Thanks a lot.
Your command worked perfectly.

---

