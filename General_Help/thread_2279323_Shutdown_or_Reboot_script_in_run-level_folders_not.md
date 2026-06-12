---
title: "Shutdown or Reboot script in run-level folders not working"
date: 2015-05-22
forum: General Help
---

### Post by weyland42 on 2015-05-22
[FONT=Helvetica]I want to know what was running in all workspaces when I close the system down, so I've put this script in /etc/init.d and symlinked it in /etc/rc0.d and rc6.d (which are for shutdown and reboot).
[/FONT]
[FONT=courier new]#!/bin/bash
# WY 2015-05-22 Run at shutdown or reboot to save workspace status. Runs from /etc/init.d
#               Symlink to /etc/init.d is in /etc/rc0.d and rc6.d

wmctrl -l | sort > /home/weyland/0-lenb/exec/K99aa-shutdown.save[/FONT]

[FONT=courier new]exit 0[/FONT]

[FONT=Helvetica]The script file symlink is *K99aa-shutdown*. It is set as executable. It works fine if I run it manually.
[/FONT]
[FONT=Helvetica]The machine reboots OK, but nothing gets saved. What am I doing wrong?

[This is Ubuntu 15.04 Mate on AMD64.][/FONT]

---

### Post by weyland42 on 2015-05-23
Could this problem be because of this? [https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers) It looks a lot more complex than what I'm trying to do the "old" way.

It includes the following . . .

[h=1][COLOR=#a52a2a]System Init Daemon[/COLOR][/h][COLOR=#a52a2a][FONT=Ubuntu Beta][/FONT][FONT=Ubuntu Beta][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta][COLOR=#a52a2a]This has changed as part of the Ubuntu 15.04 devel cycle.[/COLOR][/FONT][/COLOR]

---

### Post by weyland42 on 2015-05-23
I should add that I've also tried K01 as a prefix for the symlink, but that doesn't work either.

---

### Post by weyland42 on 2015-05-25
[FONT=Helvetica]Systemd appears in the Monitor Processes list, so I'm guessing that init.d and the other .d files are not used.

[/FONT]
[FONT=Helvetica]I gather from [http://unix.stackexchange.com/questions/47695/how-to-write-startup-script-for-systemd](http://unix.stackexchange.com/questions/47695/how-to-write-startup-script-for-systemd) that systemd is controlled in a much different way, which isn't exactly clear to me. Not sure if I want to make the effort to delve into it yet. I thought it would be a trivial task to automatically run a script at shutdown or reboot. Far from it, it seems.[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica](If only I could run VM/CMS on this machine, all my troubles would be over. Happy days.)[/FONT]

---

