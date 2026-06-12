---
title: "rm -d &amp; rmdir --ignore dont work?"
date: 2008-03-25
forum: General Help
---

### Post by seeker1458 on 2008-03-25
I cant delete a directory called cisco.d...how come?

```
sysadm@syslog:~$ cd /var/log
sysadm@syslog:/var/log$ dir
acpid            daemon.log.0     installer         scrollkeeper.log.1
acpid.1.gz       daemon.log.1.gz  kern.log          scrollkeeper.log.2
acpid.2.gz       daemon.log.2.gz  kern.log.0        syslog
acpid.3.gz       daemon.log.3.gz  kern.log.1.gz     syslog.0
acpid.4.gz       debug            kern.log.2.gz     syslog.1.gz
apparmor         debug.0          kern.log.3.gz     syslog.4.gz
apport.log       debug.1.gz       lastlog           syslog.5.gz
apport.log.1     debug.2.gz       lpr.log           syslog.6.gz
apport.log.2.gz  debug.3.gz       mail.err          syslog.7.gz
apt              dist-upgrade     mail.info         udev
auth.log         dmesg            mail.log          unattended-upgrades
auth.log.0       dmesg.0          mail.warn         user.log
auth.log.1.gz    dmesg.1.gz       messages          user.log.0
auth.log.2.gz    dmesg.2.gz       messages.0        user.log.1.gz
auth.log.3.gz    dmesg.3.gz       messages.1.gz     user.log.2.gz
bittorrent       dmesg.4.gz       messages.2.gz     user.log.3.gz
boot             dpkg.log         messages.3.gz     wtmp
bootstrap.log    dpkg.log.1       network.d         wtmp.1
btmp             enterprise.log   news              wvdialconf.log
btmp.1           faillog          ntpstats          Xorg.0.log
cisco.d          fontconfig.log   pycentral.log     Xorg.0.log.old
cups             fsck             samba             Xorg.20.log
daemon.log       gdm              scrollkeeper.log
sysadm@syslog:/var/log$ sudo rm -d cisco.d
rm: cannot remove `cisco.d': Is a directory
sysadm@syslog:/var/log$ sudo rmdir cisco.d
rmdir: cisco.d: Directory not empty
sysadm@syslog:/var/log$ sudo rmdir --ignore cisco.d
sysadm@syslog:/var/log$ dir
acpid            auth.log.0     daemon.log       dmesg           fsck           mail.info      pycentral.log       syslog.7.gz          Xorg.0.log
acpid.1.gz       auth.log.1.gz  daemon.log.0     dmesg.0         gdm            mail.log       samba               udev                 Xorg.0.log.old
acpid.2.gz       auth.log.2.gz  daemon.log.1.gz  dmesg.1.gz      installer      mail.warn      scrollkeeper.log    unattended-upgrades  Xorg.20.log
acpid.3.gz       auth.log.3.gz  daemon.log.2.gz  dmesg.2.gz      kern.log       messages       scrollkeeper.log.1  user.log
acpid.4.gz       bittorrent     daemon.log.3.gz  dmesg.3.gz      kern.log.0     messages.0     scrollkeeper.log.2  user.log.0
apparmor         boot           debug            dmesg.4.gz      kern.log.1.gz  messages.1.gz  syslog              user.log.1.gz
apport.log       bootstrap.log  debug.0          dpkg.log        kern.log.2.gz  messages.2.gz  syslog.0            user.log.2.gz
apport.log.1     btmp           debug.1.gz       dpkg.log.1      kern.log.3.gz  messages.3.gz  syslog.1.gz         user.log.3.gz
apport.log.2.gz  btmp.1         debug.2.gz       enterprise.log  lastlog        network.d      syslog.4.gz         wtmp
apt              cisco.d        debug.3.gz       faillog         lpr.log        news           syslog.5.gz         wtmp.1
auth.log         cups           dist-upgrade     fontconfig.log  mail.err       ntpstats       syslog.6.gz         wvdialconf.log
sysadm@syslog:/var/log$ 

```

---

### Post by zxan on 2008-03-25
Try this instead:
```
 sudo rm -R cisco.d

```
-R =  remove directories and their contents recursively

---

### Post by seeker1458 on 2008-03-25
k that worked...I thought the -d switch was used to delete directories?

---

### Post by seeker1458 on 2008-03-25
K, I see now that it says UNLINK files.....blah blah blah....only if you system supports unlinking for non-empty directories.  What exactly is unlinking?

---

### Post by sujoy on 2008-03-25
> **seeker1458 said:**
> k that worked...I thought the -d switch was used to delete directories?

whenever in doubt see the man pages or the GNU info pages

$ man <command>
or
$ info <command>

---

### Post by seeker1458 on 2008-03-25
> **sujoy said:**
> whenever in doubt see the man pages or the GNU info pages
>

see above

---

### Post by stchman on 2008-03-25
> **seeker1458 said:**
> k that worked...I thought the -d switch was used to delete directories?

The rmdir command does not delete directories that are populated.  The rm -r command will delete anything.  Be careful when using the rm command as it can be disastrous if mis used.

When I want to delete a directory I use the

rm -r -f

command as this deletes all sub folders no matter the permissions.

---

