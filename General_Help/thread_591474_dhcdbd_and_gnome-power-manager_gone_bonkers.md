---
title: "dhcdbd and gnome-power-manager gone bonkers"
date: 2007-10-25
forum: General Help
---

### Post by peabody on 2007-10-25
I was troubling shooting NetworkManager and I tried restarting the dbus service via the command line with "sudo /etc/init.d/dbus restart".  Now, ever since, dhcdbd has stopped working and the following messages appear in /var/log/message:

```

Oct 25 12:50:24 peabody-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 25 12:50:24 peabody-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers

```

I was only able to get an IP address by running the dhclient command manually with NetworkManager running.

Also, gnome-power-manager cannot detect batter life anymore.  It simply says the laptop is running on AC power, whether it's plugged in or not.

This is really driving me nuts.  I did nothing other than restart the dbus service while logged in.  I can't imagine why this would have had the effect it did.

Cold booting does not solve the problem.

---

### Post by Kakihara on 2007-10-30
I've got the same problem with gnome-power-manager as you.
It doesn't recognize battery, even if I can read its info in /proc/acpi/ ...
if I restart dbus ( #/etc/init.d/dbus restart ), NetworkManager disconnects and connects again and gnome-power-manager quits. When I start gnome-power-manareg manually now,  it works nicely, showing my battery state. But it works only until next reboot.

more nfo: my system is upgraded step by step from dapper to gutsy. This issue appeared in feisty after some upgrade, i believe(or maybe I did the /etc/init.d/dbus restart, don't remember).
solution should be simple .. probably some configuration files of dbus, gnome-power-manager, or init scripts...?

---

### Post by noynac on 2007-10-30
I've been getting that error message for a long time. There's a bug report on it at:

[https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360](https://bugs.launchpad.net/ubuntu/+source/dhcdbd/+bug/93360)

---

### Post by peabody on 2007-10-30
Just a quick update on this issue.  It looks like the dhcdbd issues were a false alarm.  I checked my previous logs and that error message looks like it had been around much earlier than I thought (well before I restarted my dbus service).  My dhcp issues resolved themselves, it looks like it was other network trouble.  I've since moved to Wicd (which I love and will be sticking with: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)). However, the gnome-power-manager issue remains.  I've discovered that restarting the hal service fixes the problem and is much less destructive than restarting the dbus service (which will kill just about anything connected to it).  The fact that restarting hal fixes the problem seems to indicate to me that there's an issue in the order services are being started.  Between Edgy to Feisty I believe "upstart" was deployed, which was a new init process.  Not sure if this is something to do with upstart or the scripts in the run levels, or something to do with how the services connected to dbus run, but my guess is the root of the problem will be found there.

Still, it amazes me that no one's found a resolution to this issue yet.  Here's another bug report more closely related to the gnome-power-manager issue:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/39413)

No resolution to speak of, other than restarting hal.

---

