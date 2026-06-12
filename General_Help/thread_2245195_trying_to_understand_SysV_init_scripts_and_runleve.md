---
title: "trying to understand SysV init scripts and runlevels"
date: 2014-09-21
forum: General Help
---

### Post by terminator14 on 2014-09-21
**Edit:** While most of the threads I make apply to Ubuntu, even though I'm using Debian, I just realized that recent versions of ubuntu use upstart. To be clear, this question is referring to the generic SysV system that most linux distros have been using for years, until recently.

**Original Question:**
One thing I never understood is the way SysV uses symlinks in the /etc/rcX.d/ folders. It would makes sense if, for every init script in /etc/init.d, there would either be a K##... symlink or an S##... symlink in EVERY /etc/rcX.d/ folder (for every runlevel), so that whenever you switch to a specific runlevel, no matter what your previous runlevel was, it would always end up with the same daemons running. This is not the case.

This is my Debian 7's /etc/rc1.d/ folder:

```
lrwxrwxrwx 1 root root  20 May 14 19:37 K01alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx 1 root root  13 May 14 19:37 K01atd -> ../init.d/atd
lrwxrwxrwx 1 root root  19 May 14 19:37 K01bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  15 May 14 19:37 K01exim4 -> ../init.d/exim4
lrwxrwxrwx 1 root root  14 May 14 19:37 K01gdm3 -> ../init.d/gdm3
lrwxrwxrwx 1 root root  19 May 14 19:37 K01minissdpd -> ../init.d/minissdpd
lrwxrwxrwx 1 root root  21 May 14 19:11 K01mpt-statusd -> ../init.d/mpt-statusd
lrwxrwxrwx 1 root root  23 Sep 21 17:44 K01open-vm-tools -> ../init.d/open-vm-tools
lrwxrwxrwx 1 root root  20 May 14 19:37 K01pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  15 May 14 19:37 K01saned -> ../init.d/saned
lrwxrwxrwx 1 root root  27 May 14 19:37 K01speech-dispatcher -> ../init.d/speech-dispatcher
lrwxrwxrwx 1 root root  22 May 14 19:37 K02avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  25 May 14 19:37 K02network-manager -> ../init.d/network-manager
lrwxrwxrwx 1 root root  17 May 14 19:37 K04rsyslog -> ../init.d/rsyslog
lrwxrwxrwx 1 root root  20 May 14 19:37 K06nfs-common -> ../init.d/nfs-common
lrwxrwxrwx 1 root root  17 May 14 19:37 K06rpcbind -> ../init.d/rpcbind
-rw-r--r-- 1 root root 369 Oct 15  2012 README
lrwxrwxrwx 1 root root  19 May 14 19:06 S01killprocs -> ../init.d/killprocs
lrwxrwxrwx 1 root root  14 May 14 19:06 S01motd -> ../init.d/motd
lrwxrwxrwx 1 root root  18 May 14 19:37 S20bootlogs -> ../init.d/bootlogs
lrwxrwxrwx 1 root root  16 May 14 19:37 S21single -> ../init.d/single

```

This is its /etc/rc2.d/ folder:

```
lrwxrwxrwx 1 root root  32 May 14 19:58 K01vmware-tools-thinprint -> ../init.d/vmware-tools-thinprint
-rw-r--r-- 1 root root 677 Jul 14  2013 README
lrwxrwxrwx 1 root root  14 May 14 19:06 S01motd -> ../init.d/motd
lrwxrwxrwx 1 root root  17 May 14 19:37 S13rpcbind -> ../init.d/rpcbind
lrwxrwxrwx 1 root root  20 May 14 19:37 S14nfs-common -> ../init.d/nfs-common
lrwxrwxrwx 1 root root  24 May 14 19:37 S16binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root  23 Sep 21 17:44 S16open-vm-tools -> ../init.d/open-vm-tools
lrwxrwxrwx 1 root root  17 May 14 19:37 S16rsyslog -> ../init.d/rsyslog
lrwxrwxrwx 1 root root  14 May 14 19:37 S16sudo -> ../init.d/sudo
lrwxrwxrwx 1 root root  15 May 14 19:37 S17acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  17 May 14 19:37 S17anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 May 14 19:37 S17atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 May 14 19:37 S17cron -> ../init.d/cron
lrwxrwxrwx 1 root root  14 May 14 19:37 S17dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  15 May 14 19:37 S17exim4 -> ../init.d/exim4
lrwxrwxrwx 1 root root  21 May 14 19:37 S17mpt-statusd -> ../init.d/mpt-statusd
lrwxrwxrwx 1 root root  15 Aug 27 17:50 S17rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  27 May 14 19:37 S17speech-dispatcher -> ../init.d/speech-dispatcher
lrwxrwxrwx 1 root root  13 May 14 19:37 S17ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root  22 May 14 19:37 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  19 May 14 19:37 S18bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  25 May 14 19:37 S18network-manager -> ../init.d/network-manager
lrwxrwxrwx 1 root root  14 May 14 19:37 S19gdm3 -> ../init.d/gdm3
lrwxrwxrwx 1 root root  20 May 14 19:37 S19pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  15 May 14 19:37 S19saned -> ../init.d/saned
lrwxrwxrwx 1 root root  18 May 14 19:37 S20bootlogs -> ../init.d/bootlogs
lrwxrwxrwx 1 root root  19 May 14 19:37 S21minissdpd -> ../init.d/minissdpd
lrwxrwxrwx 1 root root  18 May 14 19:37 S21rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 May 14 19:37 S21rmnologin -> ../init.d/rmnologin
lrwxrwxrwx 1 root root  34 May 14 21:18 S57vmware-tools-thinprint -> /etc/init.d/vmware-tools-thinprint

```
There are a ton of links that only appear in one folder, or the other. As far as I can tell, this would create inconsistencies between the daemons that are running when you boot directly into a particular runlevel, and when you switch to that runlevel from a different one. It also seems like it would be very easy to fix by simply including a K## or S## script for every script in /etc/init.d in every /etc/rcX.d folder, as previously mentioned.

Ex. of the problem I see using the 2 folders above:

If you were to boot into runlevel 2, /etc/rc2.d/S17acpid would run the ACPID daemon. If you then switch to runlevel 1, there is no kill symlink for apcid in /etc/rc1.d/ so acpid would keep running.
If you boot directly into runlevel 1 though, it would NOT start acpid, since there is no start symlink for it in /etc/rc1.d

If you were to boot into runlevel 2, /etc/rc2.d/S17cron would start the cron daemon. If you then switch to runlevel 1, there is no kill symlink for cron in /etc/rc1.d/ so cron would keep running.
If you boot directly into runlevel 1 though, it would NOT start the cron daemon, since there is no start symlink for it in /etc/rc1.d

There are a ton of other examples of this.

Some of the scripts in /etc/init.d/ do NOT run daemons, and are meant to be run only once at boot, like anacron. In such cases, it would make sense that there would be no need for a kill symlink when you change runlevels, but it seems like it would be much, much simpler if there was a kill symlink anyway in such cases, and the init script (/etc/init.d/anacron in this case) just exited when it receives the "stop" argument without doing anything.

Why the inconsistency? Am I missing something?

---

### Post by ian-weisser on 2014-09-23
Back in those days it was the sysadmin's job to manually customize the runlevels, and the services for each runlevel, based on the need.

Runlevels predate Ubuntu, and the current implementations of it-should-run-out-of-the-box.

Also, some of the scripts in /etc/init.d may be there for packaging convenience only, and superseded by /etc/init jobs.

---

### Post by terminator14 on 2014-09-23
> **ian-weisser said:**
> Back in those days it was the sysadmin's job to manually customize the runlevels, and the services for each runlevel, based on the need.

Runlevels predate Ubuntu, and the current implementations of it-should-run-out-of-the-box.

Also, some of the scripts in /etc/init.d may be there for packaging convenience only, and superseded by /etc/init jobs.

They may predate Ubuntu, but Ubuntu used to use them, and distros like Debian 7 still do. SysV and its runlevels are on the LPIC exam that I plan to take, so I need to know how it works.

---

### Post by terminator14 on 2014-09-24
When you switch runlevels, /etc/init.d/rc does checking on the scripts present in the previous runlevel and the scripts present in the current runlevel to decide which daemons should remain running, and which ones should stop.

What then is the purpose of Kill scripts?

If you just had regular old symlinks in each runlevel directory (/etc/rcX.d/) that had exactly the same name as the scripts in /etc/init.d/, then /etc/init.d/rc could easily just run two loops:

Loop 1: Check which scripts need to be passed the "stop" arg by seeing which scripts that are in the previous runlevel dir are not present in the current runlevel directory.
Loop 2: Check which scripts need to be passed the "start" arg by seeing which scripts that are in the current runlevel dir are not present in the previous runlevel directory.

That's it. Easy system. I could probably code this in under 100 lines in bash.
Instead, there's kill scripts, and start scripts, and some complicated process of what runs when, and why.

---

