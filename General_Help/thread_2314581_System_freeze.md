---
title: "System freeze"
date: 2016-02-22
forum: General Help
---

### Post by ABCzeta on 2016-02-22
[COLOR=#111111][FONT=Ubuntu]on my new pc i've installed xubuntu 15.10. My mobo is an asrock q1900m pro3 with integrated cpu (intel celeron j1900) and gpu.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Sometime my system freezes, here a log file captured after two freezes today:

```
[/FONT][/COLOR]
Feb 22 11:33:33 alveare systemd-logind[678]: New seat seat0.
Feb 22 11:33:33 alveare systemd-logind[678]: Watching system buttons on /dev/input/event2 (Power Button)
Feb 22 11:33:33 alveare systemd-logind[678]: Watching system buttons on /dev/input/event3 (Video Bus)
Feb 22 11:33:33 alveare systemd-logind[678]: Watching system buttons on /dev/input/event0 (Power Button)
Feb 22 11:33:33 alveare systemd-logind[678]: Watching system buttons on /dev/input/event1 (Sleep Button)
Feb 22 11:33:33 alveare lightdm: pam_unix(lightdm-autologin:session): session opened for user angelo by (uid=0)
Feb 22 11:33:33 alveare systemd: pam_unix(systemd-user:session): session opened for user angelo by (uid=0)
Feb 22 11:33:33 alveare systemd-logind[678]: New session c1 of user angelo.
Feb 22 11:33:34 alveare gnome-keyring-daemon[902]: couldn't access control socket: /run/user/1000/keyring/control: File o directory non esistente
Feb 22 11:33:35 alveare dbus[632]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.26" (uid=0 pid=1014 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.7" (uid=0 pid=655 comm="/usr/sbin/NetworkManager --no-daemon ")
Feb 22 11:33:36 alveare polkitd(authority=local): Registered Authentication Agent for unix-session:c1 (system bus name :1.36 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale it_IT.UTF-8)
Feb 22 11:33:36 alveare pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Feb 22 11:33:36 alveare pkexec: pam_systemd(polkit-1:session): Cannot create session: Already running in a session
Feb 22 11:33:36 alveare pkexec[1301]: angelo: Executing command [USER=root] [TTY=unknown] [CWD=/] [COMMAND=/usr/sbin/xfpm-power-backlight-helper --set-brightness-switch 0]
Feb 22 11:34:01 alveare dbus[632]: [system] Failed to activate service 'org.bluez': timed out
Feb 22 11:38:47 alveare systemd-logind[580]: New seat seat0.
Feb 22 11:38:47 alveare systemd-logind[580]: Watching system buttons on /dev/input/event2 (Power Button)
Feb 22 11:38:47 alveare systemd-logind[580]: Watching system buttons on /dev/input/event3 (Video Bus)
Feb 22 11:38:47 alveare systemd-logind[580]: Watching system buttons on /dev/input/event0 (Power Button)
Feb 22 11:38:47 alveare systemd-logind[580]: Watching system buttons on /dev/input/event1 (Sleep Button)
Feb 22 11:38:48 alveare lightdm: pam_unix(lightdm-autologin:session): session opened for user angelo by (uid=0)
Feb 22 11:38:48 alveare systemd: pam_unix(systemd-user:session): session opened for user angelo by (uid=0)
Feb 22 11:38:48 alveare systemd-logind[580]: New session c1 of user angelo.
Feb 22 11:38:48 alveare gnome-keyring-daemon[903]: couldn't access control socket: /run/user/1000/keyring/control: File o directory non esistente
Feb 22 11:38:49 alveare dbus[610]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.29" (uid=0 pid=1029 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.4" (uid=0 pid=595 comm="/usr/sbin/NetworkManager --no-daemon ")
Feb 22 11:38:51 alveare polkitd(authority=local): Registered Authentication Agent for unix-session:c1 (system bus name :1.35 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale it_IT.UTF-8)
Feb 22 11:38:51 alveare pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Feb 22 11:38:51 alveare pkexec: pam_systemd(polkit-1:session): Cannot create session: Already running in a session
Feb 22 11:38:51 alveare pkexec[1301]: angelo: Executing command [USER=root] [TTY=unknown] [CWD=/] [COMMAND=/usr/sbin/xfpm-power-backlight-helper --set-brightness-switch 0]
Feb 22 11:39:16 alveare dbus[610]: [system] Failed to activate service 'org.bluez': timed out
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@Feb 22 11:42:24 alveare systemd-logind[642]: New seat seat0.
Feb 22 11:42:24 alveare systemd-logind[642]: Watching system buttons on /dev/input/event2 (Power Button)
Feb 22 11:42:24 alveare systemd-logind[642]: Watching system buttons on /dev/input/event3 (Video Bus)
Feb 22 11:42:24 alveare systemd-logind[642]: Watching system buttons on /dev/input/event0 (Power Button)
Feb 22 11:42:24 alveare systemd-logind[642]: Watching system buttons on /dev/input/event1 (Sleep Button)
Feb 22 11:42:25 alveare lightdm: pam_unix(lightdm-autologin:session): session opened for user angelo by (uid=0)
Feb 22 11:42:25 alveare systemd-logind[642]: New session c1 of user angelo.
Feb 22 11:42:25 alveare systemd: pam_unix(systemd-user:session): session opened for user angelo by (uid=0)
Feb 22 11:42:25 alveare gnome-keyring-daemon[876]: couldn't access control socket: /run/user/1000/keyring/control: File o directory non esistente
Feb 22 11:42:27 alveare pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Feb 22 11:42:27 alveare pkexec: pam_systemd(polkit-1:session): Cannot create session: Already running in a session
Feb 22 11:42:27 alveare pkexec[1014]: angelo: Executing command [USER=root] [TTY=unknown] [CWD=/] [COMMAND=/usr/sbin/xfpm-power-backlight-helper --set-brightness-switch 0]
Feb 22 11:42:27 alveare polkitd(authority=local): Registered Authentication Agent for unix-session:c1 (system bus name :1.39 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale it_IT.UTF-8)
Feb 22 11:42:29 alveare dbus[650]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.46" (uid=0 pid=1119 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.6" (uid=0 pid=609 comm="/usr/sbin/NetworkManager --no-daemon ")
Feb 22 11:42:53 alveare dbus[650]: [system] Failed to activate service 'org.bluez': timed out [COLOR=#111111][FONT=Ubuntu][FONT=Consolas](END)
[/FONT][/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]

What can i do? Please help, thanks.

---

### Post by T.J. on 2016-02-24
Welcome!

I'm sorry, but the log is not very useful. =( Random freezes, however can usually be traced to power management (ACPI or the CPU governor).  Sadly, not all mobo chips are created equal, and no matter how much the programmers try, some are just plain weird. Have you tried starting the system with acpi=off specified?  If you aren't familiar with it, please let me know.

---

### Post by kyutums on 2016-03-18
It seems that you need these kernel options:
> reboot=pci 
intel_idle.max_cstate=1 

Found it from this source: [https://forums.gentoo.org/viewtopic-t-1006426.html?sid=11f3fc9e72025841afec1cd5237fa208](https://forums.gentoo.org/viewtopic-t-1006426.html?sid=11f3fc9e72025841afec1cd5237fa208)

---

