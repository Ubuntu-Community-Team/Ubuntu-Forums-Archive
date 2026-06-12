---
title: "Adept Manager Problem it wont let me apply changes or full upgrade"
date: 2007-12-16
forum: General Help
---

### Post by jbp.imperial on 2007-12-16
at first this worked and was downloading fine, while this was going on i closed the Kontact manager then it stopped working. i closed the program and tried to open it but i got a message spelling out the fact that there already is a program using the database so i would not be able to apply changes or full upgrade. then i restart the computer and i get the same message when running adept.   i ran a command that i saw on an old post that responed with this info. Can any one help?
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 migration/1
    6 ?        00:00:00 ksoftirqd/1
    7 ?        00:00:00 watchdog/1
    8 ?        00:00:00 events/0
    9 ?        00:00:00 events/1
   10 ?        00:00:00 khelper
   11 ?        00:00:00 kthread
   14 ?        00:00:00 kblockd/0
   15 ?        00:00:00 kblockd/1
   16 ?        00:00:00 kacpid
   17 ?        00:00:00 kacpi_notify
  144 ?        00:00:00 kseriod
  177 ?        00:00:00 pdflush
  178 ?        00:00:00 pdflush
  179 ?        00:00:00 kswapd0
  180 ?        00:00:00 aio/0
  181 ?        00:00:00 aio/1
  809 ?        00:00:00 kirqd
 1671 ?        00:00:00 ata/0
 1672 ?        00:00:00 ata/1
 1677 ?        00:00:00 scsi_eh_0
 1678 ?        00:00:00 scsi_eh_1
 1762 ?        00:00:00 khubd
 1794 ?        00:00:00 khpsbpkt
 1812 ?        00:00:00 knodemgrd_0
 1865 ?        00:00:00 kjournald
 1951 ?        00:00:00 logd
 2097 ?        00:00:00 udevd
 2907 ?        00:00:00 kpsmoused
 2912 ?        00:00:00 shpchpd
 3464 ?        00:00:00 dhclient3
 3671 tty1     00:00:00 getty
 3672 tty2     00:00:00 getty
 3673 tty3     00:00:00 getty
 3674 tty4     00:00:00 getty
 3675 tty5     00:00:00 getty
 3676 tty6     00:00:00 getty
 3918 ?        00:00:00 acpid
 4013 ?        00:00:00 syslogd
 4039 ?        00:00:00 dd
 4041 ?        00:00:00 klogd
 4054 ?        00:00:00 kdm
 4084 tty7     00:00:28 Xorg
 4086 ?        00:00:00 cupsd
 4087 ?        00:00:00 kdm
 4106 ?        00:00:00 hpiod
 4109 ?        00:00:00 python
 4158 ?        00:00:00 apt-index-watch
 4174 ?        00:00:00 dbus-daemon
 4189 ?        00:00:02 hald
 4190 ?        00:00:00 hald-runner
 4196 ?        00:00:00 hald-addon-acpi
 4199 ?        00:00:00 hald-addon-keyb
 4259 ?        00:00:00 ondemand
 4301 ?        00:00:00 hcid
 4309 ?        00:00:00 sdpd
 4321 ?        00:00:00 krfcommd
 4355 ?        00:00:00 atd
 4368 ?        00:00:00 cron
 4446 ?        00:00:00 x-session-manag
 4482 ?        00:00:00 ssh-agent
 4485 ?        00:00:00 dbus-launch
 4486 ?        00:00:00 dbus-daemon
 4518 ?        00:00:00 start_kdeinit
 4519 ?        00:00:00 kdeinit
 4522 ?        00:00:00 dcopserver
 4525 ?        00:00:00 klauncher
 4527 ?        00:00:01 kded
 4533 ?        00:00:00 kwrapper
 4535 ?        00:00:00 ksmserver
 4536 ?        00:00:00 kwin
 4538 ?        00:00:01 kdesktop
 4540 ?        00:00:01 kicker
 4542 ?        00:00:00 kio_file
 4544 ?        00:00:00 kio_uiserver
 4545 ?        00:00:00 kio_thumbnail
 4546 ?        00:00:00 kio_system
 4547 ?        00:00:00 kio_trash
 4560 ?        00:00:02 artsd
 4562 ?        00:00:00 kaccess
 4566 ?        00:00:00 kmix
 4567 ?        00:00:01 katapult
 4573 ?        00:00:00 aspell
 4575 ?        00:00:00 guidance-power-
 4577 ?        00:00:00 passkey-agent
 4581 ?        00:00:00 kbluetoothd
 4582 ?        00:00:00 knotify
 4584 ?        00:00:00 klipper
 4586 ?        00:00:01 guidance-power-
 4592 ?        00:00:09 konqueror
 4596 ?        00:00:00 dhclient3
 4604 ?        00:00:00 kio_file
 4605 ?        00:00:00 kio_file
 4606 ?        00:00:00 kio_file
 4607 ?        00:00:00 kio_file
 4608 ?        00:00:00 kio_http
 4612 ?        00:00:00 kio_http
 4613 ?        00:00:00 kio_http
 4617 ?        00:00:00 kio_http
 4624 ?        00:00:00 kio_http
 4629 ?        00:00:00 kio_http
 4638 ?        00:00:00 kio_http
 4646 ?        00:00:00 kio_http
 4647 ?        00:00:00 kio_http
 4677 ?        00:00:00 kio_http
 4681 ?        00:00:01 konsole
 4682 pts/1    00:00:00 bash
 4698 pts/1    00:00:00 ps

---

### Post by p_quarles on 2007-12-16
I think I see the problem. It looks like apt-index-watch is the process locking the database. To fix it, try killing the process:
```
killall apt-index-watch
```
Try that first, but I'm guessing you'll need root privileges to end that process, so if it doesn't work:
```
sudo killall apt-index-watch
```
Then, try running Adept Update again.

---

### Post by jbp.imperial on 2007-12-17
Ok, i tried  that it replied 'no process killed' then i started Adept i still get this message
"You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one."
can anyone help?:confused:

---

### Post by p_quarles on 2007-12-17
> **jbp.imperial said:**
> Ok, i tried  that it replied 'no process killed' then i started Adept i still get this message
"You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one."
can anyone help?:confused:
That's kinda strange, I have to say. You ran it with "sudo" as per my second suggestion, right?

Anyway, if you could post the output of the following two commands, I might be able to help:
```
sudo apt-get update && sudo apt-get upgrade
```
and 
```
ps -aux
```
The first command will attempt to do the same thing the Adept Update program was trying to do, but may provide more feedback. The second command will give more information about the processes that are currently running on your system.

---

### Post by CurtyD13 on 2007-12-17
I had the same problem
```
sudo dpkg --configure -a
```
seems to clear it up

---

