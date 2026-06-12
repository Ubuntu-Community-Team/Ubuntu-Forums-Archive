---
title: "avahi-daemon timestamp not taking timezone into account"
date: 2008-03-25
forum: General Help
---

### Post by boozer_2 on 2008-03-25
The avahi-daemon timestamps are wrong in the syslog.  They show up as GMT instead of CDT like everything else.  Is there a way to change this?  Makes sorting things by time really annoying, and incorrect.


Mar 25 15:42:49 r avahi-daemon[5414]: Got SIGTERM, quitting.
Mar 25 15:42:49 r avahi-daemon[5414]: Leaving mDNS multicast group on interface vmnet1.IPv4 with address 192.168.66.1.
Mar 25 15:42:49 r avahi-daemon[5414]: Leaving mDNS multicast group on interface vmnet8.IPv4 with address 172.16.173.1.
Mar 25 15:42:49 r avahi-daemon[5414]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.171.250.109.
Mar 25 10:42:52 r kernel: [67508.169931] /dev/vmmon[19450]: Module vmmon: unloaded
Mar 25 10:42:52 r kernel: [67508.314165] bridge-eth0: down
Mar 25 10:42:52 r kernel: [67508.314418] bridge-eth0: detached

---

### Post by dcstar on 2008-03-26
> **boozer_2 said:**
> The avahi-daemon timestamps are wrong in the syslog.  They show up as GMT instead of CDT like everything else.  Is there a way to change this?  Makes sorting things by time really annoying, and incorrect.


Mar 25 15:42:49 r avahi-daemon[5414]: Got SIGTERM, quitting.
Mar 25 15:42:49 r avahi-daemon[5414]: Leaving mDNS multicast group on interface vmnet1.IPv4 with address 192.168.66.1.
Mar 25 15:42:49 r avahi-daemon[5414]: Leaving mDNS multicast group on interface vmnet8.IPv4 with address 172.16.173.1.
Mar 25 15:42:49 r avahi-daemon[5414]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.171.250.109.
Mar 25 10:42:52 r kernel: [67508.169931] /dev/vmmon[19450]: Module vmmon: unloaded
Mar 25 10:42:52 r kernel: [67508.314165] bridge-eth0: down
Mar 25 10:42:52 r kernel: [67508.314418] bridge-eth0: detached

Check your Gnome desktop "Use UTC" setting - it may be wrong for your system's underlying timezone setting (or vice-versa).

---

### Post by boozer_2 on 2008-03-26
Actually, I'm using Kubuntu... so the KDE interface.  I have specified CDT timezone along along with NTP.  Thing is that my time and date is correct on the display... also every other daemon/process logs with with correct time.  I mean all log entries have the correct time except this one process, avahi-daemon logs with UTC for some reason.

---

