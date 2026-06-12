---
title: "problem with apt and software install"
date: 2015-03-10
forum: General Help
---

### Post by fynn2 on 2015-03-10
Hello,

something screwed up with my APT-GET. we are 3 people using this system so I don`t really know what happened.. I get the following errors:

```

(synaptic:8736): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
Selecting previously unselected package grub-common.
(Reading database ... 360902 files and directories currently installed.)
Preparing to unpack .../grub-common_2.02~beta2-15_amd64.deb ...
Unpacking grub-common (2.02~beta2-15) ...
Preparing to unpack .../grub2-common_2.02~beta2-15_amd64.deb ...
Unpacking grub2-common (2.02~beta2-15) over (2.02~beta2-15) ...
Processing triggers for man-db (2.7.0.2-2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for install-info (5.2.0.dfsg.1-4) ...
Setting up procps (1:3.3.9-1ubuntu5.2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of systemd:
 systemd depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package systemd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-systemd:amd64:
 libpam-systemd:amd64 depends on systemd (= 208-8ubuntu8.2); however:
  Package systemd is not configured yet.

dpkg: error processing package libpam-systemd:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-daemon:
 cups-daemon depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cups-daemon (--configure):
 dependency problems - leaving unconfigureNo apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                      No apport report written because the error message indicates it's a follow-up error from a previous failure.
                  No apport report written because MaxReports has already been reached
      No apport report written because MaxReports has already been reached
                                                                          d
Setting up ntp (1:4.2.6.p5+dfsg-3ubuntu2.14.10.2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package ntp (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Setting up ike (2.2.1+dfsg-2ubuntu1) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package ike (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Setting up rsyslog (7.4.4-1ubuntu11.2) ...
The user `syslog' is already a member of `adm'.
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Setting up cgmanager (0.32-4ubuntu1.3) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package cgmanager (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up apport (2.14.7-0ubuntu8.2) ...
No apport report written because MaxReports has already been reached
                                                                    insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package apport (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
 apport-gtk depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Setting up at (3.1.14-1ubuntu2) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package at (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on procps (>= 1:3.3.2); however:
  Package procps is not configured yet.

dpkg: error processing package clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of cups-core-drivers:
 cups-core-drivers depends on cups-daemon (>= 1.7.5-3ubuntu3.1); however:
  Package cups-daemon is not configured yet.

dpkg: error processing package cups-core-drivers (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of cups:
 cups depends on cups-core-drivers (>= 1.7.5-3ubuntu3.1); however:
  Package cups-core-drivers is not configured yet.
 cups depends on cups-daemon (>= 1.7.5-3ubuntu3.1); however:
  Package cups-daemon is not configured yet.
 cups depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cups (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of dropbox:
 dropbox depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package dropbox (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Setting up gnustep-base-runtime (1.24.6-2ubuntu1) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package gnustep-base-runtime (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Setting up openvpn (2.3.2-9ubuntu1.1) ...
 * Restarting virtual private network daemon(s)...                               *   No VPN is running.
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package openvpn (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up spamassassin (3.4.0-3ubuntu2.1) ...
No apport report written because MaxReports has already been reached
                                                                    insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (empty) of script `spamassassin' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `spamassassin' overrides LSB defaults (0 1 6).
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$aNo apport report written because MaxReports has already been reached
                                                                           No apport report written because MaxReports has already been reached
                                                               No apport report written because MaxReports has already been reached
                                                   ll' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package spamassassin (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sa-compile:
 sa-compile depends on spamassassin (>= 3.3.2-8); however:
  Package spamassassin is not configured yet.

dpkg: error processing package sa-compile (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on udev (>= 149); however:
  Package udev is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
Setting up anytun (0.3.4-2build3) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package anytun (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on at; however:
  Package at is not configured yet.
 lsb-core depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package lsb-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-graphics (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-cxx (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of lsb-multimedia:
 lsb-multimedia depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-multimedia (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of lsb-desktop:
 lsb-desktop depends on lsb-graphics (>= 4.1+Debian11ubuntu8); however:
  Package lsb-graphics is not configured yet.
 lsb-desktop depends on lsb-multimedia (>= 4.1+Debian11ubuntu8); however:
  Package lsb-multimedia is not configured yet.

dpkg: error processing package lsb-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of lsb-printing:
 lsb-printing depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-printing (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of lsb-languages:
 lsb-languages depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-languages (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics (>= 4.1+Debian11ubuntu8); however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx (>= 4.1+Debian11ubuntu8); however:
  Package lsb-cxx is not configured yet.
 lsb depends on lsb-desktop (>= 4.1+Debian11ubuntu8); however:
  Package lsb-desktop is not configured yet.
 lsb depends on lsb-printing (>= 4.1+Debian11ubuntu8); however:
  Package lsb-printing is not configured yet.
 lsb depends on lsb-languages (>= 4.1+Debian11ubuntu8); however:
  Package lsb-languages is not configured yet.

dpkg: error processing package lsb (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of epson-inkjet-printer-escpr:
 epson-inkjet-printer-escpr depends on lsb (>= 3.2); however:
  Package lsb is not configured yet.

dpkg: error processing package epson-inkjet-printer-escpr (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ike-qtgui:
 ike-qtgui depends on ike; however:
  Package ike is not configured yet.

dpkg: error processing package ike-qtgui (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Setting up ipsec-tools (1:0.8.0-14ubuntu4) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package ipsec-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of iscan-data:
 iscan-data depends on udev (>= 0.105-4); however:
  Package udev is not configured yet.

dpkg: error processing package iscan-data (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Setting up grub-common (2.02~beta2-15) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.02~beta2-15); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 procps
 udev
 systemd
 libpam-systemd:amd64
 cups-daemon
 ntp
 ike
 rsyslog
 cgmanager
 apport
 apport-gtk
 at
 clamav-freshclam
 cups-core-drivers
 cups
 dropbox
 gnustep-base-runtime
 openvpn
 spamassassin
 sa-compile
 xserver-xorg-core
 anytun
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb-multimedia
 lsb-desktop
 lsb-printing
 lsb-languages
 lsb
 epson-inkjet-printer-escpr
 ike-qtgui
 ipsec-tools
 iscan-data
 grub-common
 grub2-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up procps (1:3.3.9-1ubuntu5.2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package lsb-core (--configure):
 dependency problems - leaving unconfigured
Setting up gnustep-base-runtime (1.24.6-2ubuntu1) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package gnustep-base-runtime (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up grub-common (2.02~beta2-15) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lsb-multimedia:
 lsb-multimedia depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-multimedia (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-printing:
 lsb-printing depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-printing (--configure):
 dependency problems - leaving unconfigured
Setting up anytun (0.3.4-2build3) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package anytun (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ike (2.2.1+dfsg-2ubuntu1) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package ike (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on procps (>= 1:3.3.2); however:
  Package procps is not configured yet.

dpkg: error processing package clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
Setting up at (3.1.14-1ubuntu2) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package at (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ntp (1:4.2.6.p5+dfsg-3ubuntu2.14.10.2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package ntp (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up spamassassin (3.4.0-3ubuntu2.1) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (empty) of script `spamassassin' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `spamassassin' overrides LSB defaults (0 1 6).
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package spamassassin (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dropbox:
 dropbox depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package dropbox (--configure):
 dependency problems - leaving unconfigured
Setting up openvpn (2.3.2-9ubuntu1.1) ...
 * Restarting virtual private network daemon(s)...                               *   No VPN is running.
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package openvpn (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ipsec-tools (1:0.8.0-14ubuntu4) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package ipsec-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lsb-desktop:
 lsb-desktop depends on lsb-multimedia (>= 4.1+Debian11ubuntu8); however:
  Package lsb-multimedia is not configured yet.

dpkg: error processing package lsb-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-daemon:
 cups-daemon depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cups-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics (>= 4.1+Debian11ubuntu8); however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-desktop (>= 4.1+Debian11ubuntu8); however:
  Package lsb-desktop is not configured yet.
 lsb depends on lsb-printing (>= 4.1+Debian11ubuntu8); however:
  Package lsb-printing is not configured yet.

dpkg: error processing package lsb (--configure):
 dependency problems - leaving unconfigured
Setting up cgmanager (0.32-4ubuntu1.3) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package cgmanager (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.02~beta2-15); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-languages:
 lsb-languages depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-languages (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of udev:
 udev depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package udev (--configure):
 dependency problems - leaving unconfigured
Setting up rsyslog (7.4.4-1ubuntu11.2) ...
The user `syslog' is already a member of `adm'.
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up apport (2.14.7-0ubuntu8.2) ...
insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plexmediaserver'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plexmediaserver'
insserv: There is a loop between service ondemand and procps if started
insserv:  loop involving service procps at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service .depend.stop and hwclock if started
insserv:  loop involving service hwclock at depth 1
insserv:  loop involving service checkroot at depth 3
insserv:  loop involving service mountdevsubfs at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service irqbalance at depth 1
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service .depend.stop if started
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 4
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting .depend.stop depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package apport (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cups:
 cups depends on cups-daemon (>= 1.7.5-3ubuntu3.1); however:
  Package cups-daemon is not configured yet.
 cups depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing package cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core (>= 4.1+Debian11ubuntu8); however:
  Package lsb-core is not configured yet.

dpkg: error processing package lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of epson-inkjet-printer-escpr:
 epson-inkjet-printer-escpr depends on lsb (>= 3.2); however:
  Package lsb is not configured yet.

dpkg: error processing package epson-inkjet-printer-escpr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on udev (>= 149); however:
  Package udev is not configured yet.

dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ike-qtgui:
 ike-qtgui depends on ike; however:
  Package ike is not configured yet.

dpkg: error processing package ike-qtgui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-core-drivers:
 cups-core-drivers depends on cups-daemon (>= 1.7.5-3ubuntu3.1); however:
  Package cups-daemon is not configured yet.

dpkg: error processing package cups-core-drivers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of iscan-data:
 iscan-data depends on udev (>= 0.105-4); however:
  Package udev is not configured yet.

dpkg: error processing package iscan-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sa-compile:
 sa-compile depends on spamassassin (>= 3.3.2-8); however:
  Package spamassassin is not configured yet.

dpkg: error processing package sa-compile (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of systemd:
 systemd depends on udev; however:
  Package udev is not configured yet.

dpkg: error processing package systemd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-systemd:amd64:
 libpam-systemd:amd64 depends on systemd (= 208-8ubuntu8.2); however:
  Package systemd is not configured yet.

dpkg: error processing package libpam-systemd:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 procps
 apport-gtk
 lsb-core
 gnustep-base-runtime
 grub-common
 lsb-multimedia
 lsb-printing
 anytun
 ike
 clamav-freshclam
 at
 ntp
 spamassassin
 dropbox
 openvpn
 ipsec-tools
 lsb-desktop
 lsb-graphics
 cups-daemon
 lsb
 cgmanager
 grub2-common
 lsb-languages
 udev
 rsyslog
 apport
 cups
 lsb-cxx
 epson-inkjet-printer-escpr
 xserver-xorg-core
 ike-qtgui
 cups-core-drivers
 iscan-data
 sa-compile
 systemd
 libpam-systemd:amd64


```


any idea how to fix this?
thank you!!

fynn

---

### Post by QIII on 2015-03-10
You have this under Other OS.

Is this not a flavor of Ubuntu?

If not, what is it?

---

### Post by fynn2 on 2015-03-10
sorry I`m new here and wasn`t sure where to post, its Lubuntu version.

---

### Post by QIII on 2015-03-10
OK.  Moved to ***General Help.***

Lubuntu is an official flavor of Ubuntu.

---

### Post by jeffsilverm on 2015-03-20
Fynn,

I am trying to install cups on UbuntuMate 14.10 and I have a similar error.  The error message I get is
insserv: Starting cups depends on ondemand and therefore on system facility `$all' which can not be true!

At first I thought this was an error in cups, but seeing your message suggests to me that the problem might be in insserv.  I found [http://forums.debian.net/viewtopic.php?f=30&t=53192](http://forums.debian.net/viewtopic.php?f=30&t=53192) which suggests that the problem might be a conflicting program, but the article doesn't say how to find the program that might be conflicting with it.

I wrote a bug about it, [https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/1432824](https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/1432824) .  However, I think I wrote a poor bug, and I am going to add this conversation to it and see if that might be helpful.

---

### Post by ian-weisser on 2015-03-20
> **fynn2 said:**
> insserv: warning: script 'K20.depend.stop' missing LSB tags and overrides
insserv: warning: script 'plexmediaserver' missing LSB tags and overrides

Looks lot like [LP:#1385817]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1385817")

The solution is to add LSB headers to /etc/init.d/plexmediaserver.
Is /etc/init.d/K20.depend.stop really an init script? If it's an init script, it needs LSB tags, too. If it's not an init script, it probably does not belong in /etc/init.d

---

### Post by fynn2 on 2015-03-26
Hi,

I did remove plex but the problem is still present. tried to configure the packages but still get the same messages and seems like the list of dependency problems is getting longer, any idea?

---

### Post by ian-weisser on 2015-03-26
You removed plex, but you still get an inserv warning about plexmediaserver?
Init scripts are in /etc. Did you **purge** the package?

---

