---
title: "How to find cause of system hang?"
date: 2007-02-22
forum: General Help
---

### Post by Dr_Snapid on 2007-02-22
My ubuntu 6.06 (i386) system hangs unexpectedly. Usually it is when I am away from the machine for a long time but sometimes while i am working. Everything freezes except the mouse, which I can move, but cannot click anything.

If I press ctrl+alt+bksp it kills x as expected and I get a command line login.

I can type but the system does not accept anything. When i press enter i get a new line and can keep typing! I can type right down the page.... but am forced to do a hardware reset to reboot. Even CTRL+ALT+DEL doesnt reboot. :mad: 

Is there some sort of log file which might help me find out why this is happening? Something I can refer to after the reboot to see what went wrong?

---

### Post by Ramses de Norre on 2007-02-22
There are many, depending on what caused the crash they can contain info about it:

~/.xsession-erorrs
/var/log/syslog
/var/log/messages
/var/log/Xorg.0.log.old
...

---

### Post by Dr_Snapid on 2007-04-11
In var/log/messages, there seems to be an entry called 'MARK' which just gets added every 20 mins, presumably just to show logging was working. My PC was on overnight last night, and here is what the log shows:

Apr 11 23:22:38 localhost -- MARK --
Apr 11 23:42:38 localhost -- MARK --
Apr 12 00:02:38 localhost -- MARK --
Apr 12 00:22:38 localhost -- MARK --
Apr 12 00:42:39 localhost -- MARK --
Apr 12 01:02:39 localhost -- MARK --
Apr 12 01:22:39 localhost -- MARK --
Apr 12 01:42:39 localhost -- MARK --
Apr 12 02:02:40 localhost -- MARK --
Apr 12 02:24:14 localhost -- MARK --
Apr 12 07:35:38 localhost syslogd 1.4.1#17ubuntu7: restart.
Apr 12 07:35:38 localhost kernel: Inspecting /boot/System.map-2.6.15-28-386

I presume this means that soon after the last MARK at about 2:30am, the system hung. At 7:30 I was forced to reboot. During the 2:30am to 7:30am period, none of the system logs have anything. I have checked kern.log, syslog, and debug.

All i can think of is some kind of hardware failure, but the weird thing is, if it happens when my screensaver is on, when i move the mouse i get the password prompt (screen locked) and I can enter my password, but then it freezes at the 'checking password' message and i never get my desktop to come back. The keyboard is not frozen, nor the mouse. So the system is alive, but dead...

---

