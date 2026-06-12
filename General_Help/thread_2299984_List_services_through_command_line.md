---
title: "List services through command line"
date: 2015-10-22
forum: General Help
---

### Post by james_l2 on 2015-10-22
Hey,

I would like to list the services that automatically start on boot.


I have tried the [COLOR=#111111][FONT=Consolas]initctl list[/FONT][/COLOR] which shows all current services but I'd like to see what starts up automatically on boot.. is there a command for this?[COLOR=#111111][FONT=Consolas]

Ubuntu 14.04[/FONT][/COLOR]

---

### Post by shadytv on 2015-10-22
The services that boot on startup are stored under /etc/init.d/ you can delete the files that you don't want to run on startup **BUT BE CAREFUL**, If you're not sure about it don't delete it.

---

### Post by tgalati4 on 2015-10-23
Don't forget that additional modules get loaded in /etc/modules and extra services in /etc/rc.local.

---

### Post by SeijiSensei on 2015-10-23
/etc/init.d contains the startup scripts for all services; the ones that actually start up at boot have symlinks in the directory /etc/rc2.d.  The directories /etc/rc3.d through /etc/rc5.d contain the same list.  On my Kubuntu 14.04 workstation I have
```

rw-r--r-- 1 root root 677 Jun 14 23:31 README
lrwxrwxrwx 1 root root  26 Jun  7 23:53 S20clamav-freshclam -> ../init.d/clamav-freshclam
lrwxrwxrwx 1 root root  20 Mar 18  2015 S20kerneloops -> ../init.d/kerneloops
lrwxrwxrwx 1 root root  18 Sep 12 16:27 S20minidlna -> ../init.d/minidlna
lrwxrwxrwx 1 root root  27 Apr  6  2015 S20nfs-kernel-server -> ../init.d/nfs-kernel-server
lrwxrwxrwx 1 root root  15 Mar 18  2015 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  23 Apr  2  2015 S20smartmontools -> ../init.d/smartmontools
lrwxrwxrwx 1 root root  17 Mar 18  2015 S20vboxdrv -> ../init.d/vboxdrv
lrwxrwxrwx 1 root root  31 Mar 18  2015 S35vboxautostart-service -> ../init.d/vboxautostart-service
lrwxrwxrwx 1 root root  33 Mar 18  2015 S35vboxballoonctrl-service -> ../init.d/vboxballoonctrl-service
lrwxrwxrwx 1 root root  25 Mar 18  2015 S35vboxweb-service -> ../init.d/vboxweb-service
lrwxrwxrwx 1 root root  15 Mar 18  2015 S50saned -> ../init.d/saned
lrwxrwxrwx 1 root root  19 Mar 18  2015 S70dns-clean -> ../init.d/dns-clean
lrwxrwxrwx 1 root root  18 Mar 18  2015 S70pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx 1 root root  17 May  7 21:44 S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  21 Mar 18  2015 S99grub-common -> ../init.d/grub-common
lrwxrwxrwx 1 root root  18 Mar 18  2015 S99ondemand -> ../init.d/ondemand
lrwxrwxrwx 1 root root  18 Mar 18  2015 S99rc.local -> ../init.d/rc.local

```
On a server the list would be very different.

All this changes on systems using systemd.  I avoided dealing with that up until a few months' back when I put up a CentOS 7 server for a client.  I'm still pretty much a noob when it comes to systemd.

---

