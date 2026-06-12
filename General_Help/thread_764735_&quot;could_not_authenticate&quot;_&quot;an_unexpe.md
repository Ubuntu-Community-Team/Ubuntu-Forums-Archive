---
title: "&quot;could not authenticate&quot; &quot;an unexpected error has occurred&quot;"
date: 2008-04-24
forum: General Help
---

### Post by aaron552 on 2008-04-24
Hi, I have had a problem with ubuntu hardy for a while now. Whenever I try to access something that uses gnome's new authorization system, i will either get "could not authenticate" "an unexpected error has occurred" or no response when i click the "unlock" button. Sometimes i even get "The configuration could not be loaded" "You are not allowed to access system configuration"

I am the only user of this system.
When I run polkit-gnome-authorization in a terminal i get:
** (polkit-gnome-authorization:12823): CRITICAL **: dbus_g_connection_get_connection: assertion `gconnection' failed
process 12823: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.

** (polkit-gnome-authorization:12823): CRITICAL **: dbus_g_connection_get_connection: assertion `gconnection' failed
process 12823: arguments to dbus_connection_send() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3081.
This is normally a bug in some application using the D-Bus library.
Segmentation fault

I need help, this is more than just annoying.

---

### Post by Ingenium on 2008-04-27
I'm having the same issue. Have you found any solutions yet? If it matters, I upgraded from gutsy.

---

### Post by aaron552 on 2008-04-28
I have been hardy since the original beta. I've tried reinstalling dbus and polkit, but that hasn't worked

---

### Post by Ingenium on 2008-04-29
> **aaron552 said:**
> I have been hardy since the original beta. I've tried reinstalling dbus and polkit, but that hasn't worked

I tried the same thing. Maybe it's in one of the configuration files since people who did fresh installs don't seem to have this problem. Is there a way to erase the configuration files and recreate them without purging the package?

---

### Post by happynix on 2008-05-08
Try looking here: [Polkit hell]("http://ubuntuforums.org/showthread.php?p=4866207")

Sounds like the same dbus/hal race condition problem.

---

### Post by Ingenium on 2008-05-08
Yeah that did it. I noticed an update I got the other day fixed it, and when I checked just now hal had already been changed to 24. Thanks.

---

### Post by BuhDuh on 2009-10-17
Sorry to reopen old wounds, but I can't find a definitive answer to
the error "could not authenticate" "an unexpected error has occurred".
I am fairly new to any flavor of *nix, but have been using Ubuntu
as my workstation since 2005. Recently my stepson asked if I could
create a LAMP server for him so I grabbed Jaunty server and did a clean
install, selecting 'ssh server' as the target. I then followed the excellent
[http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2)
but omitted the ispconfig, as I felt it was overkill. Everything went fine
until I started running into problems configuring ufw - I just couldn't
seem to wrap my head around the esoteric incantations required in a shell
to get iptables working properly, so (I can hear gasps and shrieks of outrage)
I did 

'sudo apt-get install --no-install-recommends ubuntu-desktop'
'sudo gdm'

Ahh! a gui I was familiar with! Configuring with gufw was a snap, and I soon
had the ports open which I needed to continue, that is until I tried to unlock
'Users Settings' in System->Administration->Users and Groups. Whammie!
So I am left stumbling around trying as hard as I can to learn how to do
sysadmin from the shell, which I'm finding quite painful.
Anyway, here is some additional info based on previous threads:

Output of 'ls -al /etc/rc2.d' (edited for clarity)

S01policykit             -> ../init.d/policykit
S10acpid                 -> ../init.d/acpid
S10apmd                  -> ../init.d/apmd
S10sysklogd              -> ../init.d/sysklogd
S11klogd                 -> ../init.d/klogd
S12dbus                  -> ../init.d/dbus
S16ssh                   -> ../init.d/ssh
S17mysql-ndb-mgm         -> ../init.d/mysql-ndb-mgm
S18mysql-ndb             -> ../init.d/mysql-ndb
S19mysql                 -> ../init.d/mysql
S20courier-authdaemon    -> ../init.d/courier-authdaemon
S20courier-imap          -> ../init.d/courier-imap
S20courier-imap-ssl      -> ../init.d/courier-imap-ssl
S20courier-pop           -> ../init.d/courier-pop
S20courier-pop-ssl       -> ../init.d/courier-pop-ssl
S20postfix               -> ../init.d/postfix
S20saslauthd             -> ../init.d/saslauthd
S23ntp                   -> ../init.d/ntp
S24hal                   -> ../init.d/hal
S30gdm                   -> ../init.d/gdm
S50cups                  -> ../init.d/cups
S50pulseaudio            -> ../init.d/pulseaudio
S50rsync                 -> ../init.d/rsync
S50system-tools-backends -> ../init.d/system-tools-backends
S70bootlogs.sh           -> ../init.d/bootlogs.sh
S70dns-clean             -> ../init.d/dns-clean
S70pppd-dns              -> ../init.d/pppd-dns
S89anacron               -> ../init.d/anacron
S89atd                   -> ../init.d/atd
S89cron                  -> ../init.d/cron
S91apache2               -> ../init.d/apache2
S98usplash               -> ../init.d/usplash
S99fetchmail             -> ../init.d/fetchmail
S99ondemand              -> ../init.d/ondemand
S99rc.local              -> ../init.d/rc.local
S99rmnologin             -> ../init.d/rmnologin
S99stop-readahead        -> ../init.d/stop-readahead

'tail -f /var/log/messages | grep -v UFW' showed no output when
the error is displayed, and nothing was recorded in /var/log/auth.log

---

