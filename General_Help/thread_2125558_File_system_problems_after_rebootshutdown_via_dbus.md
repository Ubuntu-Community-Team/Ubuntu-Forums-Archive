---
title: "File system problems after reboot/shutdown via dbus."
date: 2013-03-14
forum: General Help
---

### Post by Artif on 2013-03-14
There are some opportunities to shutdown a system via command line without special permissions in sudoers or else. Dbus may be used. It just works a year or two ago. This week I have tried them over SSH via sudo.

The system is headless, it is hard to see what happened exactly. If one guide me on what a logs I must check - I'll do it.

The facts are: after one reboot and one shutdown, in both cases, I got filesystem problems, with subsequent boot problems (headless machine...). After one reboot (problem is still under investigation) the system was  not able to show files from '/home'. After reboot it become OK. Another issue - after one shutdown I got lost device in MD RAID1, to be mounted as '/home', which prevents the system to boot. I do not tried dbus more.

'shutdown -[Pr] now' do not break the system, with 'reboot' and 'poweroff' the system also have no problems. I think this is not hardware issue. SMART is OK, powersupply is strong enough and voltage is OK, data and power cables are fine.


May be any one can give an advice or guides on what may be wrong with the commands processing by the system. Please give me an advice.


The comands are the first two from the list:
```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart
dbus-send --system --print-reply --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
dbus-send --system --print-reply --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Hibernate

```

The system setup is: Ubuntu **12.04** "command line system" installation from alternate CD, with subsequent 'apt-get install lxde lxdm'. No other special modification were applied. The root ext4 filesystem is on LVM over MD RAID0, '/home' ext4 is directly on MD RAID1. LVM volume had a spare volume with several Gb of changes (it may lead to some fatal timeouts while boot on some distributions). Now spare volume is recreated, it do not have much "backup records".

The lost device from RAID1 was readded into array. It seems valuable information was not lost.

---

### Post by tgalati4 on 2013-03-14
Perhaps using DBUS to shut down the system with mdadm is not a good idea.  Obviously, certain processes don't get shut down cleanly, which results in file system corruption.  Look through the log files in /var/log especially syslog and see if you can find any file system-related error messages.  Why can't the main user perform *sudo shutdown -h now*?

---

### Post by Artif on 2013-03-15
Thank you for the guide lines, I'll try them and report a result.  > **tgalati4 said:**
> Why can't the main user perform *sudo shutdown -h now*? Because this needs a password to be entered under a cameras in public area, because all the users must have super password (to be writen down on back side of their keyboard). On the other hand - because sudoers file, with unevident syntax, with path and passwords complicity, must be changed(recreated) on every system. Now I'm using sudoers.   

When user is at physical console, the Dbus commands will do the job out of the box without superuser's password (as it was 1-3 years ago). But it seems they may have unwanted effects (I'm not shure; it is not easy now to debug it...).

---

### Post by schragge on 2013-03-15
As there's an advice how to disable **Ctrl**+**Alt**+**Del** ([uhelp]12.04/serverguide/console-security.html#disable-ctrl-alt-delete[/uhelp]) I guess you can adapt it to perform *shutdown -h now* instead.

---

