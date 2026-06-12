---
title: "Ubuntu freezes at first boot, but second is OK"
date: 2016-11-11
forum: General Help
---

### Post by petko0954 on 2016-11-11
Ubuntu 16.04 always freezes after first time I turn on computer (1-3min after all is started), but when I restart computer(using SysRQ key) everything is OK (it doesnt freeze yet after second boot). Sometimes the mouse pointer slow down before the freeze. Logs are looking Ok, but I post anything if you want. This is only error I found in logs:
```
pc kernel: [   84.349208] audit: type=1400 audit(1478879068.090:40): apparmor="DENIED" operation="open" profile="/usr/lib/*/mediascanner-2.0/mediascanner-extractor" name=2F686F6D652F70657465722F4F6272C3A17A6B792F57616C6C7061706572732F77616C6C7061706572732F77616C6C70617065722D36383434323320286BC3B3706961292E6A7067 pid=2162 comm="mediascanner-ex" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
pc kernel: [   85.014272] hfsplus: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
pc kernel: [  551.224083] perf interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50000




```

---

### Post by kracheck on 2016-11-17
Checking log files is indeed your first stop. I'm just wondering, is the log you posted the log message of the current boot or that of a previous boot ?

I believe Ubuntu 16.04 stores logs in /run/log/journal by default. Please check 
[http://www.dsm.fordham.edu/cgi-bin/man-cgi.pl?topic=journald.conf&ampsect=5](http://www.dsm.fordham.edu/cgi-bin/man-cgi.pl?topic=journald.conf&ampsect=5) 
in particular the "Options" section. 

Because /run is volatile the journal log messages are not retained between boots. 

In order to have log messages from previous boots execute below steps :
#nano /etc/systemd/journald.conf
In the [journal] section uncomment Storage=auto and change to Storage=persistent
# mkdir /var/log/journal
# systemd-tmpfiles --create --prefix /var/log/journal
# systemctl restart systemd-journald

Other possible issues one might explore in order to solve this :
-run top to monitor what happens before the freeze : [http://manpages.ubuntu.com/manpages/precise/man1/top.1.html](http://manpages.ubuntu.com/manpages/precise/man1/top.1.html)
-use diferent video drivers (for instance install nvidia proprietary instead of nouveau)
-Boot via GRUB2 with different kernel parameters. Google for freezes related to 
intel_idle.max_cstate=1, freezes related to ACPI (e.g. ACPI=off), etc.
-Google for Freeze and BIOS settings. Check posts related to Fast Boot, Secure boot

---

