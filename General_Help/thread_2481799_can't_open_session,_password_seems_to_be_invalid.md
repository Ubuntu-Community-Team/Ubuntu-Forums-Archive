---
title: "can't open session, password seems to be invalid"
date: 2022-12-09
forum: General Help
---

### Post by Minus63 on 2022-12-09
Hello

All my ubuntus are in an active directory domain

and from time to time my users can't log in

here are the errors I have in /etc/var/auth.log

[HTML]Dec  6 08:23:15 DellLat56248 dbus-daemon[1713]: [system] Failed to activate service 'org.freedesktop.fwupd': timed out (service_start_timeout=25000ms)
Dec  6 08:23:15 DellLat56248 PackageKit: uid 236606719 is trying to obtain org.freedesktop.packagekit.system-sources-refresh auth (only_trusted:0)
Dec  6 08:23:15 DellLat56248 PackageKit: uid 236606719 obtained auth for org.freedesktop.packagekit.system-sources-refresh
Dec  6 08:23:40 DellLat56248 dbus-daemon[1713]: [system] Failed to activate service 'org.freedesktop.fwupd': timed out (service_start_timeout=25000ms)
Dec  6 08:25:27 DellLat56248 CRON[2012]: pam_unix(cron:session): session closed for user root
Dec  6 08:25:36 DellLat56248 gdm-password]: pam_unix(gdm-password:auth): authentication failure; logname= uid=0 euid=0 tty=/dev/tty1 ruser= rhost=  user=myuser
Dec  6 08:25:36 DellLat56248 gdm-password]: pam_sss(gdm-password:auth): authentication success; logname= uid=0 euid=0 tty=/dev/tty1 ruser= rhost= user=myuser
Dec  6 08:25:37 DellLat56248 gdm-password]: gkr-pam: unlocked login keyring
Dec  6 08:25:38 DellLat56248 pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=236606719)
Dec  6 08:25:38 DellLat56248 pkexec[7879]: myuser: Executing command [USER=root] [TTY=unknown] [CWD=/home/myuser] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Dec  6 08:25:56 DellLat56248 gnome-keyring-daemon[2805]: asked to register item /org/freedesktop/secrets/collection/login/1, but it's already registered
Dec  6 08:26:07 DellLat56248 dbus-daemon[1713]: [system] Failed to activate service 'org.freedesktop.fwupd': timed out (service_start_timeout=25000ms)
Dec  6 08:26:07 DellLat56248 PackageKit: uid 236606719 is trying to obtain org.freedesktop.packagekit.system-sources-refresh auth (only_trusted:0)
Dec  6 08:26:07 DellLat56248 PackageKit: uid 236606719 obtained auth for org.freedesktop.packagekit.system-sources-refresh[/HTML]

sometimes a simple reboot and everything is back to normal

[HTML]root@DellLat56248:/etc/pam.d# vi gdm-password
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_succeed_if.so user != root quiet_success
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
# SELinux needs to be the first session rule. This ensures that any
# lingering context has been cleared. Without this it is possible
# that a module could execute code in the wrong domain.
session [success=ok ignore=ignore module_unknown=ignore default=bad]        pam_selinux.so close
session required        pam_loginuid.so
# SELinux needs to intervene at login time to ensure that the process
# starts in the proper default security context. Only sessions which are
# intended to run in the user's context should be run after this.
# pam_selinux.so changes the SELinux context of the used TTY and configures
# SELinux in order to transition to the user context with the next execve()
# call.
session [success=ok ignore=ignore module_unknown=ignore default=bad]        pam_selinux.so open
session optional        pam_keyinit.so force revoke
session required        pam_limits.so
session required        pam_env.so readenv=1
session required        pam_env.so readenv=1 user_readenv=1 envfile=/etc/default/locale
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password
~[/HTML]

here is the gdm-password file since it seems that it is the one that causes the problem

Thank you for your help

Greetings

---

### Post by MAFoElffen on 2022-12-09
I don't think it's your /etc/pam.d/gdm-password file as you assumed, as mine is exactly the same and I have no problems...

What about your /etc/krb5.conf file?

Are you getting kerberos ticket leases assigned okay?

You said active domain... With what as your DC?

---

### Post by Minus63 on 2022-12-12
Hi

I don't have /etc/krb5.conf file 

I use this script for my domain integration: [https://github.com/PierreGode/Linux-Active-Directory-join-script/blob/master/ADconnection.sh](https://github.com/PierreGode/Linux-Active-Directory-join-script/blob/master/ADconnection.sh)

My DC is a windows server 2019.

---

