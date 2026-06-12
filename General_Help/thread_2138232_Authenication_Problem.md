---
title: "Authenication Problem"
date: 2013-04-23
forum: General Help
---

### Post by binarynut on 2013-04-23
Can't authenicate when trying run root apps.
I have run "sudo passwd root" and set root password.

below is the /var/log/auth.log

```
Apr 22 17:00:52 linaro-alip sudo:   linaro : TTY=pts/1 ; PWD=/home/linaro ; USER=root ; COMMAND=/usr/sbin/synaptic
Apr 22 17:00:52 linaro-alip sudo: pam_unix(sudo:session): session opened for user root by (uid=1000)
Apr 22 17:05:39 linaro-alip polkit-agent-helper-1[1487]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=linaro rhost=  user=linaro
Apr 22 17:06:05 linaro-alip polkit-agent-helper-1[1489]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=linaro rhost=  user=linaro
Apr 22 17:06:34 linaro-alip polkit-agent-helper-1[1490]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=linaro rhost=  user=linaro
Apr 22 17:06:37 linaro-alip polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session3 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for unix-process:1463:217237 [time-admin] (owned by unix-user:linaro)
Apr 22 17:09:01 linaro-alip polkit-agent-helper-1[1491]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=linaro rhost=  user=linaro
Apr 22 17:09:19 linaro-alip polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session3 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for unix-process:1463:217237 [time-admin] (owned by unix-user:linaro)
Apr 22 17:10:00 linaro-alip sudo:   linaro : TTY=pts/3 ; PWD=/home/linaro ; USER=root ; COMMAND=/usr/bin/passwd root
Apr 22 17:10:00 linaro-alip sudo: pam_unix(sudo:session): session opened for user root by (uid=1000)
Apr 22 17:10:38 linaro-alip passwd[1517]: pam_unix(passwd:chauthtok): password changed for root
Apr 22 17:10:38 linaro-alip sudo: pam_unix(sudo:session): session closed for user root
Apr 22 17:11:28 linaro-alip polkit-agent-helper-1[1518]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=linaro rhost=  user=linaro
Apr 22 17:12:08 linaro-alip polkit-agent-helper-1[1519]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=linaro rhost=  user=linaro
Apr 22 17:13:11 linaro-alip polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session3 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for unix-process:1463:217237 [time-admin] (owned by unix-user:linaro)
Apr 22 17:13:34 linaro-alip sudo: pam_unix(sudo:session): session closed for user root
Apr 22 17:17:02 linaro-alip CRON[1582]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 22 17:17:02 linaro-alip CRON[1582]: pam_unix(cron:session): session closed for user root
Apr 22 18:17:01 linaro-alip CRON[1685]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 22 18:17:01 linaro-alip CRON[1685]: pam_unix(cron:session): session closed for user root
Apr 22 19:17:01 linaro-alip CRON[1967]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 22 19:17:01 linaro-alip CRON[1967]: pam_unix(cron:session): session closed for user root
Apr 22 20:17:01 linaro-alip CRON[1980]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 22 20:17:01 linaro-alip CRON[1980]: pam_unix(cron:session): session closed for user root
Apr 22 21:17:01 linaro-alip CRON[1995]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 22 21:17:01 linaro-alip CRON[1995]: pam_unix(cron:session): session closed for user root
Apr 22 22:17:01 linaro-alip CRON[2012]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 22 22:17:01 linaro-alip CRON[2012]: pam_unix(cron:session): session closed for user root
Apr 22 23:17:01 linaro-alip CRON[2029]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 22 23:17:01 linaro-alip CRON[2029]: pam_unix(cron:session): session closed for user root
Apr 22 23:46:41 linaro-alip polkit-agent-helper-1[2077]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=linaro rhost=  user=linaro
Apr 22 23:47:04 linaro-alip polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session3 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for unix-process:2062:2624645 [time-admin] (owned by unix-user:linaro)
Apr 22 23:48:21 linaro-alip sudo:   linaro : TTY=unknown ; PWD=/home/linaro ; USER=root ; COMMAND=/usr/bin/pengrotate NM
Apr 22 23:48:21 linaro-alip sudo: pam_unix(sudo:session): session opened for user root by (uid=1000)
Apr 22 23:48:22 linaro-alip lightdm: pam_unix(lightdm-autologin:session): session closed for user linaro
Apr 22 23:48:22 linaro-alip polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session3 (system bus name :1.13, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale C.UTF-8) (disconnected from bus)
Apr 22 23:48:23 linaro-alip sudo: pam_unix(sudo:session): session closed for user root
Apr 22 23:48:24 linaro-alip lightdm: pam_unix(lightdm-autologin:session): session opened for user linaro by (uid=0)
Apr 22 23:48:24 linaro-alip lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Apr 22 23:48:25 linaro-alip polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session4 (system bus name :1.45 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale C.UTF-8)
Apr 22 23:53:42 linaro-alip login[384]: pam_unix(login:session): session opened for user root by LOGIN(uid=0)
Apr 22 23:53:43 linaro-alip login[457]: pam_unix(login:session): session opened for user root by (uid=0)
Apr 22 23:53:43 linaro-alip login[553]: ROOT LOGIN  on '/dev/tty1'
Apr 22 23:53:43 linaro-alip login[554]: ROOT LOGIN  on '/dev/ttyS0'
Apr 22 23:53:45 linaro-alip lightdm: pam_unix(lightdm-autologin:session): session opened for user linaro by (uid=0)
Apr 22 23:53:45 linaro-alip lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Apr 22 23:53:48 linaro-alip polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session3 (system bus name :1.13 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale C.UTF-8)
Apr 22 23:57:45 linaro-alip polkit-agent-helper-1[842]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=linaro rhost=  user=linaro
Apr 22 23:58:01 linaro-alip polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session3 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for system-bus-name::1.22 [users-admin] (owned by unix-user:linaro)
Apr 23 00:02:37 linaro-alip polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session3 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for unix-process:913:51660 [time-admin] (owned by unix-user:linaro)
Apr 23 00:06:42 linaro-alip polkit-agent-helper-1[980]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=linaro rhost=  user=linaro
Apr 23 00:06:47 linaro-alip polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session3 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for unix-process:965:74898 [time-admin] (owned by unix-user:linaro)
Apr 23 00:17:01 linaro-alip CRON[1063]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 23 00:17:02 linaro-alip CRON[1063]: pam_unix(cron:session): session closed for user root
Apr 23 00:17:39 linaro-alip polkit-agent-helper-1[1066]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=linaro rhost=  user=linaro
Apr 23 00:17:50 linaro-alip polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session3 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for unix-process:1043:138951 [time-admin] (owned by unix-user:linaro)
Apr 23 00:24:37 linaro-alip polkit-agent-helper-1[1129]: pam_unix(polkit-1:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=linaro rhost=  user=linaro
Apr 23 00:24:45 linaro-alip polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session3 FAILED to authenticate to gain authorization for action org.freedesktop.systemtoolsbackends.set for unix-process:1111:182748 [time-admin] (owned by unix-user:linaro)
```

---

