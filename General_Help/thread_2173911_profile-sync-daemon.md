---
title: "profile-sync-daemon"
date: 2013-09-11
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-09-11
I have [graysky's]("http://ubuntuforums.org/showthread.php?t=2115685") profile-sync-daemon installed since 11.04 and after a recent kernel upgrade (or at least I think the problem occured after a kernel upgrade), on trying to find the problem:

The following NEW packages will be installed:
  profile-sync-daemon
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/15.0 kB of archives.
After this operation, 82.9 kB of additional disk space will be used.
Supported
Create a snapshot of '/tmp/apt-btrfs-snapshot-mp-PgH1mz/@' in '/tmp/apt-btrfs-snapshot-mp-PgH1mz/@apt-snapshot-2013-09-11_18:12:10'
Selecting previously unselected package profile-sync-daemon.
(Reading database ... 211944 files and directories currently installed.)
Unpacking profile-sync-daemon (from .../profile-sync-daemon_5.39-1_all.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up profile-sync-daemon (5.39-1) ...
/var/lib/dpkg/info/profile-sync-daemon.postinst: 27: /etc/psd.conf: chromium: not found
dpkg: error processing profile-sync-daemon (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 profile-sync-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

I don't understand what happened and the "chromium: not found" makes no sense, because as I type this message, I'm using chromium.

---

