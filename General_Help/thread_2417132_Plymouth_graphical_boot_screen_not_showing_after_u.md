---
title: "Plymouth graphical boot screen not showing after update to 19.04"
date: 2019-04-21
forum: General Help
---

### Post by nico@nc on 2019-04-21
Hi,

After updating Ubuntu from 18.10 to 19.04, the splash screen shown after boot is displayed in text only, instead of the larger Ubuntu logo and animated dots (graphical theme):
[ATTACH=CONFIG]283071[/ATTACH]

The graphical splash screen is however shown when shutting down the computer. What could be wrong?

I have reinstalled the following packages:
```
plymouth
plymouth-label
plymouth-theme-ubuntu-logo
plymouth-theme-ubuntu-text
```

I've also checked that :
[LIST]
[*]*/usr/share/plymouth/themes/**default.grub*** links to */etc/alternatives/**default.plymouth.grub*** itself linking to */usr/share/plymouth/themes/ubuntu-logo/**ubuntu-logo.grub***
[*]*/usr/share/plymouth/themes/**default.plymouth*** links to */etc/alternatives/**default.plymouth*** itself linking to */usr/share/plymouth/themes/ubuntu-logo/**ubuntu-logo.plymouth***
[/LIST]

And finally, logs don't seem to show anything wrong:
```
me@computer:~$ journalctl -b-1 | grep -i plymouth
avril 21 14:08:15 computer systemd[1]: Starting Show Plymouth Boot Screen...
avril 21 14:08:15 computer systemd[1]: Received SIGRTMIN+20 from PID 491 (plymouthd).
avril 21 14:08:15 computer systemd[1]: Started Show Plymouth Boot Screen.
avril 21 14:08:15 computer systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
avril 21 14:08:27 computer systemd[1]: Starting Tell Plymouth To Write Out Runtime Data...
avril 21 14:08:36 computer systemd[1]: Received SIGRTMIN+20 from PID 491 (plymouthd).
avril 21 14:08:36 computer systemd[1]: plymouth-read-write.service: Succeeded.
avril 21 14:08:36 computer systemd[1]: Started Tell Plymouth To Write Out Runtime Data.
avril 21 14:09:05 computer systemd[1]: Received SIGRTMIN+21 from PID 491 (plymouthd).
avril 21 14:09:35 computer systemd[1]: Received SIGRTMIN+21 from PID 491 (plymouthd).
avril 21 14:09:35 computer systemd[1]: plymouth-quit-wait.service: Succeeded.
avril 21 14:09:35 computer systemd[1]: plymouth-start.service: Succeeded.
                                                    This package provides common:   ubuntu and budgie-desktop gsettings overrides   make QT apps look like GTK+ apps   default icon-theme for GTK+ applications   Ubuntu Budgie plymouth branding
avril 21 14:29:42 computer systemd[1]: Starting Show Plymouth Reboot Screen...
avril 21 14:29:42 computer systemd[1]: Received SIGRTMIN+20 from PID 12813 (plymouthd).
avril 21 14:29:43 computer systemd[1]: Started Show Plymouth Reboot Screen.
avril 21 14:29:45 computer systemd[1]: systemd-ask-password-plymouth.path: Succeeded.
avril 21 14:29:45 computer systemd[1]: Stopped Forward Password Requests to Plymouth Directory Watch.
```
Thank you.

---

### Post by dino99 on 2019-04-21
First, clean the system after that dist-upgrade: install/use gtkorpha, bleachbit (as root, carefully select options); reinstall the plymouth packages (with dependencies), and finally edit /etc/default/grub to check if 'spash' is still set before 'quiet'.
Then reboot, and glance at journalctl to get details if the problem still persist.

ps: i've never tested budgie, so i cant tell much (possible specific issue; maybe search on its forum if others have met that problem)

---

### Post by nico@nc on 2019-04-21
Thanks for the leads. gtkorpha and bleachbit were not helpful, and I already reinstalled plymouth packages as listed above. /etc/default/grub listed *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"*, replacing it with "splash quiet" (+ sudo update-grub) did not help either.

I'm not using Budgie, the line in the log was some gnome-software warning about an uninstalled package.

Logs are still not much helpful (as they look quite similar to a ["reference" output]("https://askubuntu.com/questions/1021861/how-to-fix-the-ubuntu-splash-loading-bar-showing-up-on-the-desktop-view") seen on another forum):
```
me@computer:~$ journalctl -b-1 | grep -i plymouth
avril 21 14:30:13 computer systemd[1]: Starting Show Plymouth Boot Screen...
avril 21 14:30:14 computer systemd[1]: Received SIGRTMIN+20 from PID 481 (plymouthd).
avril 21 14:30:15 computer systemd[1]: Started Show Plymouth Boot Screen.
avril 21 14:30:15 computer systemd[1]: Started Forward Password Requests to Plymouth Directory Watch.
avril 21 14:30:25 computer systemd[1]: Starting Tell Plymouth To Write Out Runtime Data...
avril 21 14:30:25 computer systemd[1]: Received SIGRTMIN+20 from PID 481 (plymouthd).
avril 21 14:30:25 computer systemd[1]: plymouth-read-write.service: Succeeded.
avril 21 14:30:25 computer systemd[1]: Started Tell Plymouth To Write Out Runtime Data.
avril 21 14:31:00 computer systemd[1]: Received SIGRTMIN+21 from PID 481 (plymouthd).
avril 21 14:31:34 computer systemd[1]: Received SIGRTMIN+21 from PID 481 (plymouthd).
avril 21 14:31:34 computer systemd[1]: plymouth-quit-wait.service: Succeeded.
avril 21 14:31:34 computer systemd[1]: plymouth-start.service: Succeeded.
avril 21 17:09:48 computer systemd[1]: Starting Show Plymouth Reboot Screen...
avril 21 17:09:49 computer systemd[1]: Received SIGRTMIN+20 from PID 17694 (plymouthd).
avril 21 17:09:50 computer systemd[1]: Started Show Plymouth Reboot Screen.
avril 21 17:09:54 computer systemd[1]: systemd-ask-password-plymouth.path: Succeeded.
avril 21 17:09:54 computer systemd[1]: Stopped Forward Password Requests to Plymouth Directory Watch.
```

By the way, it takes 50 seconds or so from the moment Grub screen disappears to the display of the (text) splash screen, and then another 60 seconds until the login screen appears. I haven't counted on Ubuntu 18.10, but it seems quite long, I don't know if it could be related.

---

### Post by Claus7 on 2019-05-16
Hello,

switching to gdm3 instead of lightdm might solve the issue. Maybe reinstalling one of the 2 might solve the issue as well.

Regards!

---

