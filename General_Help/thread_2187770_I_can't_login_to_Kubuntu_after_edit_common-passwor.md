---
title: "I can't login to Kubuntu after edit common-password file"
date: 2013-11-13
forum: General Help
---

### Post by ecarlevaro on 2013-11-13
I have Kubuntu 12.04.2 LTS.

I was trying to use simple passwords on normal users account so I edited **/etc/pam.d/common-password **following this how-to [http://askubuntu.com/questions/180402/how-to-set-a-short-password-on-ubuntu](http://askubuntu.com/questions/180402/how-to-set-a-short-password-on-ubuntu)

So, I deleted the parameter "obscure" from the line 
```
password        [success=2 default=ignore]      pam_unix.so obscure sha512
```

I closed and saved the file, and after that when I wanted to change user account at prompt-login window I can't login anymore, when I entered my username and password an error window appeared and it said "A critic error was produced. Look KDM log file" .

I switched to another terminal (CTRL+ALT+F1) and I tried to log in, but with all ther user's name that I tried always said "Login incorrect"

I restarted the computer and I tried again with the same results.

I entered to recovery mode (from GRUB menu) and again, the same problem, I can't log in.

I booted with a Knoppix Live-CD, and I edited the /etc/pam.d/common-password file manually, right now it looks like this:

```
 ## /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.


# Explanation of pam_unix options:
#
# The "sha512" option enables salted SHA512 passwords.  Without this option,
# the default is Unix crypt.  Prior releases used the option "md5".
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# See the pam_unix manpage for other options.


# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.


# here are the per-package modules (the "Primary" block)
password    [success=2 default=ignore]    pam_unix.so obscure sha512
password    [success=1 default=ignore]    pam_winbind.so obscure use_authtok try_first_pass
# here's the fallback if no module succeeds
password    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
password    optional    pam_gnome_keyring.so 
# end of pam-auth-update config

```

I restarted the computer and I booted Kubuntu from hard-drive but the problem is still there, I can't log in.

The last record on KDM log, located in **/var/log/kdm.log** is this:

```
X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux changueti-Aspire-5315 3.2.0-48-generic #74-Ubuntu SMP Thu Jun 6 19:43:26 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-48-generic root=UUID=98e2e2dd-da7a-487f-a7ff-8bdf8869a493 ro quiet splash vt.handoff=7
Build Date: 11 April 2013  01:05:39PM
xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 13 18:25:16 2013
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
klauncher(1230) kdemain: No DBUS session-bus found. Check if you have started the DBUS server. 
kdeinit4: Communication error with launcher. Exiting!
kdmgreet(1222)/kdecore (K*TimeZone*): KSystemTimeZones: ktimezoned initialize() D-Bus call failed:  "Not connected to D-Bus server" 


kdmgreet(1222)/kdecore (K*TimeZone*): No time zone information obtained from ktimezoned 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No existe el archivo o el directorio
QFileSystemWatcher: failed to add paths: /tmp/0144896146/.config/ibus/bus
 ddxSigGiveUp: Closing log
Server terminated successfully (0). Closing log file.

```

What can I do? 

Sorry for my english, it is not my native language.

---

