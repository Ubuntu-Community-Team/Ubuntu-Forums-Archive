---
title: "Gksudo works, pkexec works then quits."
date: 2015-12-13
forum: General Help
---

### Post by SantaFe on 2015-12-13
This is a weird one.  Last week I had an old (7 years old) Seagate 500 gig HD die on me in my Dell laptop, and replaced it with a 1 Terrabyte WD hard drive.  Installed 32 bit Xubuntu 15.10 on it (at the time I only had the 32 bit Xubuntu on my USB stick so that's what I used) and was happy as a clam.  The other day however, I noticed the Custom Action I made in Thunar to open folders as Root wasn't working.  

It used to pop up a window asking me to input my administrators password before opening the folder as root.  It used pkexec thunar %f as the command.  It would work fine after starting up, but I noticed after awhile the window wouldn't pop up.

Tried opening the terminal window and manually entering the command and got the following:
```

santafe@s****************5:~$ pkexec thunar
==== AUTHENTICATING FOR org.xfce.thunar ===
Authentication is required to run Thunar as root.
Authenticating as: santafe,,, (santafe)
Password: 
polkit-agent-helper-1: error response to PolicyKit daemon: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: No session for cookie
==== AUTHENTICATION FAILED ===
Error executing command as another user: Not authorized

This incident has been reported.
santafe@s****************5:~$ 

```
Which was weird because when I entered the same command in terminal after I booted for the first time, or rebooted when it quit on me I would get this:
```
santafe@s****************5:~$ pkexec thunar
/usr/share/themes/Blue-Bird/gtk-2.0/apps/ff.rc:16: error: invalid string constant "theme-toolbar", expected valid string constant
/usr/share/themes/Blue-Bird/gtk-2.0/apps/nautilus.rc:10: error: invalid string constant "notebook_button", expected valid string constant
santafe@s****************5:~$ 
```  And got the pop-up window & thunar opened in Root.


However I can use gksudo thunar at any time, even after pkexec decides to quit, and it works like it should, a window pops up asking me for my password & thunar opens up in root mode.  Replaced pkexec with gksudo in thunars custom action and it works as well.

Looked in the /var/log/auth.log file & clipped out this part after I rebooted to fix an earlier event.

```

Dec 13 12:53:44 santafe-Studio-1745 systemd-logind[550]: System is rebooting.
Dec 13 12:54:34 santafe-Studio-1745 systemd-logind[566]: New seat seat0.
Dec 13 12:54:34 santafe-Studio-1745 systemd-logind[566]: Watching system buttons on /dev/input/event2 (Power Button)
Dec 13 12:54:34 santafe-Studio-1745 systemd-logind[566]: Watching system buttons on /dev/input/event4 (Video Bus)
Dec 13 12:54:34 santafe-Studio-1745 systemd-logind[566]: Watching system buttons on /dev/input/event1 (Power Button)
Dec 13 12:54:34 santafe-Studio-1745 systemd-logind[566]: Watching system buttons on /dev/input/event0 (Lid Switch)
Dec 13 12:54:45 santafe-Studio-1745 dbus[568]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.16" (uid=0 pid=684 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.10" (uid=0 pid=585 comm="/usr/sbin/NetworkManager --no-daemon ")
Dec 13 12:54:47 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Dec 13 12:54:47 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet.so
Dec 13 12:54:47 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Dec 13 12:54:47 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet5.so
Dec 13 12:54:47 santafe-Studio-1745 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Dec 13 12:54:47 santafe-Studio-1745 systemd: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
Dec 13 12:54:47 santafe-Studio-1745 systemd-logind[566]: New session c1 of user lightdm.
Dec 13 12:54:50 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Dec 13 12:54:50 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet.so
Dec 13 12:54:50 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Dec 13 12:54:50 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet5.so
Dec 13 12:54:50 santafe-Studio-1745 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "santafe"
Dec 13 12:54:57 santafe-Studio-1745 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Dec 13 12:54:57 santafe-Studio-1745 lightdm: pam_unix(lightdm:session): session opened for user santafe by (uid=0)
Dec 13 12:54:57 santafe-Studio-1745 systemd: pam_unix(systemd-user:session): session opened for user santafe by (uid=0)
Dec 13 12:54:57 santafe-Studio-1745 systemd-logind[566]: New session c2 of user santafe.
Dec 13 12:54:58 santafe-Studio-1745 gnome-keyring-daemon[1012]: The SSH agent was already initialized
Dec 13 12:54:58 santafe-Studio-1745 gnome-keyring-daemon[1012]: The Secret Service was already initialized
Dec 13 12:54:58 santafe-Studio-1745 gnome-keyring-daemon[1012]: The PKCS#11 component was already initialized
Dec 13 12:54:58 santafe-Studio-1745 gnome-keyring-daemon[1012]: The Secret Service was already initialized
Dec 13 12:54:58 santafe-Studio-1745 gnome-keyring-daemon[1012]: The SSH agent was already initialized
Dec 13 12:54:58 santafe-Studio-1745 gnome-keyring-daemon[1012]: The PKCS#11 component was already initialized
Dec 13 12:54:59 santafe-Studio-1745 polkitd(authority=local): Registered Authentication Agent for unix-session:c2 (system bus name :1.42 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Dec 13 12:56:47 santafe-Studio-1745 systemd-logind[566]: Removed session c1.
Dec 13 12:56:47 santafe-Studio-1745 systemd: pam_unix(systemd-user:session): session closed for user lightdm
Dec 13 12:58:08 santafe-Studio-1745 systemd-logind[566]: System is rebooting.
Dec 13 12:58:49 santafe-Studio-1745 systemd-logind[556]: New seat seat0.
Dec 13 12:58:49 santafe-Studio-1745 systemd-logind[556]: Watching system buttons on /dev/input/event2 (Power Button)
Dec 13 12:58:49 santafe-Studio-1745 systemd-logind[556]: Watching system buttons on /dev/input/event4 (Video Bus)
Dec 13 12:58:49 santafe-Studio-1745 systemd-logind[556]: Watching system buttons on /dev/input/event1 (Power Button)
Dec 13 12:58:49 santafe-Studio-1745 systemd-logind[556]: Watching system buttons on /dev/input/event0 (Lid Switch)
Dec 13 12:59:08 santafe-Studio-1745 dbus[575]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.16" (uid=0 pid=674 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.9" (uid=0 pid=614 comm="/usr/sbin/NetworkManager --no-daemon ")
Dec 13 12:59:10 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Dec 13 12:59:10 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet.so
Dec 13 12:59:10 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Dec 13 12:59:10 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet5.so
Dec 13 12:59:10 santafe-Studio-1745 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Dec 13 12:59:10 santafe-Studio-1745 systemd: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
Dec 13 12:59:10 santafe-Studio-1745 systemd-logind[556]: New session c1 of user lightdm.
Dec 13 12:59:13 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Dec 13 12:59:13 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet.so
Dec 13 12:59:13 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Dec 13 12:59:13 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet5.so
Dec 13 12:59:13 santafe-Studio-1745 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "santafe"
Dec 13 12:59:19 santafe-Studio-1745 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Dec 13 12:59:19 santafe-Studio-1745 lightdm: pam_unix(lightdm:session): session opened for user santafe by (uid=0)
Dec 13 12:59:19 santafe-Studio-1745 systemd: pam_unix(systemd-user:session): session opened for user santafe by (uid=0)
Dec 13 12:59:19 santafe-Studio-1745 systemd-logind[556]: New session c2 of user santafe.
Dec 13 12:59:20 santafe-Studio-1745 gnome-keyring-daemon[1000]: The SSH agent was already initialized
Dec 13 12:59:20 santafe-Studio-1745 gnome-keyring-daemon[1000]: The Secret Service was already initialized
Dec 13 12:59:20 santafe-Studio-1745 gnome-keyring-daemon[1000]: The PKCS#11 component was already initialized
Dec 13 12:59:21 santafe-Studio-1745 gnome-keyring-daemon[1000]: The PKCS#11 component was already initialized
Dec 13 12:59:21 santafe-Studio-1745 polkitd(authority=local): Registered Authentication Agent for unix-session:c2 (system bus name :1.38 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Dec 13 13:00:29 santafe-Studio-1745 polkitd(authority=local): Operator of unix-session:c2 FAILED to authenticate to gain authorization for action org.xfce.thunar for unix-process:1508:12401 [/bin/sh -c pkexec thunar '/'] (owned by unix-user:santafe)
Dec 13 13:00:29 santafe-Studio-1745 pkexec[1509]: santafe: Error executing command as another user: Request dismissed [USER=root] [TTY=unknown] [CWD=/] [COMMAND=/usr/bin/thunar /]
Dec 13 13:01:10 santafe-Studio-1745 systemd-logind[556]: Removed session c1.
Dec 13 13:17:01 santafe-Studio-1745 CRON[1748]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 13 13:17:01 santafe-Studio-1745 CRON[1748]: pam_unix(cron:session): session closed for user root
Dec 13 14:17:01 santafe-Studio-1745 CRON[2024]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 13 14:17:01 santafe-Studio-1745 CRON[2024]: pam_unix(cron:session): session closed for user root
Dec 13 15:17:01 santafe-Studio-1745 CRON[2612]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 13 15:17:01 santafe-Studio-1745 CRON[2612]: pam_unix(cron:session): session closed for user root
Dec 13 16:17:01 santafe-Studio-1745 CRON[3030]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 13 16:17:01 santafe-Studio-1745 CRON[3030]: pam_unix(cron:session): session closed for user root
Dec 13 17:17:01 santafe-Studio-1745 CRON[3755]: pam_unix(cron:session): session opened for user root by (uid=0)
Dec 13 17:17:01 santafe-Studio-1745 CRON[3755]: pam_unix(cron:session): session closed for user root
Dec 13 17:24:01 santafe-Studio-1745 polkitd(authority=local): Unregistered Authentication Agent for unix-session:c2 (system bus name :1.38, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
Dec 13 17:24:01 santafe-Studio-1745 polkitd(authority=local): Operator of unix-session:c2 FAILED to authenticate to gain authorization for action org.xfce.thunar for unix-process:3785:1593741 [/bin/sh -c pkexec thunar '/'] (owned by unix-user:santafe)
Dec 13 17:24:01 santafe-Studio-1745 pkexec[3786]: santafe: Error executing command as another user: Not authorized [USER=root] [TTY=unknown] [CWD=/] [COMMAND=/usr/bin/thunar /]
Dec 13 17:24:54 santafe-Studio-1745 sudo:  santafe : TTY=pts/1 ; PWD=/home/santafe ; USER=root ; COMMAND=/usr/bin/apt-get update
Dec 13 17:24:54 santafe-Studio-1745 sudo: pam_unix(sudo:session): session opened for user root by santafe(uid=0)
Dec 13 17:25:04 santafe-Studio-1745 sudo: pam_unix(sudo:session): session closed for user root
Dec 13 17:25:04 santafe-Studio-1745 sudo:  santafe : TTY=pts/1 ; PWD=/home/santafe ; USER=root ; COMMAND=/usr/bin/apt-get upgrade
Dec 13 17:25:04 santafe-Studio-1745 sudo: pam_unix(sudo:session): session opened for user root by santafe(uid=0)
Dec 13 17:25:05 santafe-Studio-1745 sudo: pam_unix(sudo:session): session closed for user root
Dec 13 17:25:05 santafe-Studio-1745 sudo:  santafe : TTY=pts/1 ; PWD=/home/santafe ; USER=root ; COMMAND=/usr/bin/apt-get dist-upgrade
Dec 13 17:25:05 santafe-Studio-1745 sudo: pam_unix(sudo:session): session opened for user root by santafe(uid=0)
Dec 13 17:25:05 santafe-Studio-1745 sudo: pam_unix(sudo:session): session closed for user root
Dec 13 17:25:15 santafe-Studio-1745 sudo:  santafe : TTY=pts/1 ; PWD=/home/santafe ; USER=root ; COMMAND=/usr/bin/thunar
Dec 13 17:25:15 santafe-Studio-1745 sudo: pam_unix(sudo:session): session opened for user root by santafe(uid=0)
Dec 13 17:25:20 santafe-Studio-1745 sudo: pam_unix(sudo:session): session closed for user root
Dec 13 17:25:30 santafe-Studio-1745 polkitd(authority=local): Registered Authentication Agent for unix-process:3868:1598030 (system bus name :1.95 [pkexec thunar], object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Dec 13 17:25:36 santafe-Studio-1745 polkitd(authority=local): Operator of unix-process:3868:1598030 FAILED to authenticate to gain authorization for action org.xfce.thunar for unix-process:3868:1598030 [bash] (owned by unix-user:santafe)
Dec 13 17:25:36 santafe-Studio-1745 pkexec[3980]: santafe: Error executing command as another user: Not authorized [USER=root] [TTY=/dev/pts/1] [CWD=/home/santafe] [COMMAND=/usr/bin/thunar]
Dec 13 17:25:36 santafe-Studio-1745 polkitd(authority=local): Unregistered Authentication Agent for unix-process:3868:1598030 (system bus name :1.95, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Dec 13 17:25:52 santafe-Studio-1745 sudo:  santafe : TTY=unknown ; PWD=/home/santafe ; USER=root ; COMMAND=/usr/bin/thunar
Dec 13 17:25:52 santafe-Studio-1745 sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Dec 13 17:25:56 santafe-Studio-1745 sudo: pam_unix(sudo:session): session closed for user root
Dec 13 17:26:33 santafe-Studio-1745 sudo:  santafe : TTY=unknown ; PWD=/ ; USER=root ; COMMAND=/usr/bin/thunar /
Dec 13 17:26:33 santafe-Studio-1745 sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Dec 13 17:26:38 santafe-Studio-1745 sudo: pam_unix(sudo:session): session closed for user root
**********************************************
Here is where I tried opening Thunar with pkexec thunar
**********************************************
Dec 13 17:33:33 santafe-Studio-1745 polkitd(authority=local): Registered Authentication Agent for unix-process:4076:1650649 (system bus name :1.99 [pkexec thunar], object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Dec 13 17:33:42 santafe-Studio-1745 polkitd(authority=local): Operator of unix-process:4076:1650649 FAILED to authenticate to gain authorization for action org.xfce.thunar for unix-process:4076:1650649 [bash] (owned by unix-user:santafe)
Dec 13 17:33:42 santafe-Studio-1745 pkexec[4087]: santafe: Error executing command as another user: Not authorized [USER=root] [TTY=/dev/pts/1] [CWD=/home/santafe] [COMMAND=/usr/bin/thunar]
Dec 13 17:33:42 santafe-Studio-1745 polkitd(authority=local): Unregistered Authentication Agent for unix-process:4076:1650649 (system bus name :1.99, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Dec 13 17:34:20 santafe-Studio-1745 sudo:  santafe : TTY=unknown ; PWD=/home/santafe ; USER=root ; COMMAND=/usr/bin/thunar
Dec 13 17:34:20 santafe-Studio-1745 sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Dec 13 17:34:25 santafe-Studio-1745 sudo: pam_unix(sudo:session): session closed for user root
Dec 13 17:35:28 santafe-Studio-1745 lightdm: pam_unix(lightdm:session): session closed for user santafe
Dec 13 17:35:29 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Dec 13 17:35:29 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet.so
Dec 13 17:35:29 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Dec 13 17:35:29 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet5.so
Dec 13 17:35:29 santafe-Studio-1745 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Dec 13 17:35:29 santafe-Studio-1745 systemd: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
Dec 13 17:35:29 santafe-Studio-1745 systemd-logind[556]: New session c3 of user lightdm.
Dec 13 17:35:30 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Dec 13 17:35:30 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet.so
Dec 13 17:35:30 santafe-Studio-1745 lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Dec 13 17:35:30 santafe-Studio-1745 lightdm: PAM adding faulty module: pam_kwallet5.so
Dec 13 17:35:30 santafe-Studio-1745 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "santafe"
Dec 13 17:35:31 santafe-Studio-1745 systemd-logind[556]: Removed session c2.
Dec 13 17:35:31 santafe-Studio-1745 systemd: pam_unix(systemd-user:session): session closed for user santafe
Dec 13 17:35:36 santafe-Studio-1745 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Dec 13 17:35:36 santafe-Studio-1745 lightdm: pam_unix(lightdm:session): session opened for user santafe by (uid=0)
Dec 13 17:35:36 santafe-Studio-1745 systemd-logind[556]: New session c4 of user santafe.
Dec 13 17:35:36 santafe-Studio-1745 systemd: pam_unix(systemd-user:session): session opened for user santafe by (uid=0)
Dec 13 17:35:37 santafe-Studio-1745 gnome-keyring-daemon[4271]: The SSH agent was already initialized
Dec 13 17:35:37 santafe-Studio-1745 gnome-keyring-daemon[4271]: The Secret Service was already initialized
Dec 13 17:35:37 santafe-Studio-1745 gnome-keyring-daemon[4271]: The PKCS#11 component was already initialized
Dec 13 17:35:37 santafe-Studio-1745 gnome-keyring-daemon[4271]: The PKCS#11 component was already initialized
Dec 13 17:35:38 santafe-Studio-1745 polkitd(authority=local): Registered Authentication Agent for unix-session:c4 (system bus name :1.130 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Dec 13 17:36:36 santafe-Studio-1745 polkitd(authority=local): Operator of unix-session:c4 successfully authenticated as unix-user:santafe to gain ONE-SHOT authorization for action org.xfce.thunar for unix-process:4759:1668286 [bash] (owned by unix-user:santafe)
Dec 13 17:36:36 santafe-Studio-1745 pkexec: pam_unix(polkit-1:session): session opened for user root by santafe(uid=1000)
Dec 13 17:36:36 santafe-Studio-1745 pkexec: pam_systemd(polkit-1:session): Cannot create session: Already running in a session
Dec 13 17:36:36 santafe-Studio-1745 pkexec[4770]: santafe: Executing command [USER=root] [TTY=/dev/pts/2] [CWD=/home/santafe] [COMMAND=/usr/bin/thunar]
Dec 13 17:37:29 santafe-Studio-1745 systemd-logind[556]: Removed session c3.
Dec 13 17:37:29 santafe-Studio-1745 systemd: pam_unix(systemd-user:session): session closed for user lightdm


```

Trying to figure out all the references to kwallet when it's not even installed in the first place.  I also noticed it didn't seem to matter if I had SSH Key Agent & Secret Storage Service checked or unchecked.

Finally in this long and *tedious* post, I took a couple of screenshots showing what Session & Startup shows I have marked for startup at boot.
[ATTACH=CONFIG]266138[/ATTACH][ATTACH=CONFIG]266137[/ATTACH]

As it seems to be working fine using gksudo instead of pkexec, I can live with that especially since this doesn't seem to be affecting System Updates at all.  Just is a bit annoying to have pkexec stop working after a random time.

Anyone have any ideas why this is happening?  Thanks for looking at this.  ;)

---

