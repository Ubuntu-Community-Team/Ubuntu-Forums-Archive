---
title: "Dell Latitude 7389 crashes when lid is closed"
date: 2019-06-04
forum: General Help
---

### Post by nickpalmer789 on 2019-06-04
Hey, I am having some weird issues with my Dell Latitude 7389 where the OS seems to crash when I close the lid after putting the computer into a suspended state. I am running Ubuntu 18.04 with the latest and greatest updates.

Specifically, this happens when I am in suspend. I tried disabling the lid close action by editing the following in /etc/systemd/logind.conf

HandleLidSwitch=ignore

And in /etc/UPower/UPower.conf:

IgnoreLid=true

Here are the interesting logs from around the time of the crash that I have found so far:
/var/log/sylog:
Jun  4 00:42:37 nick-pc systemd[1]: Starting Restore /etc/resolv.conf if the system crashed before the ppp link was shut down...Jun  4 00:42:37 nick-pc systemd[1]: Starting LSB: automatic crash report generation...
Jun  4 00:42:37 nick-pc systemd[1]: Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down.
Jun  4 00:42:37 nick-pc apport[832]:  * Starting automatic crash report generation: apport

and 

/var/log/syslog:Jun  4 00:42:37 nick-pc dbus-daemon[844]: dbus[844]: Unknown group "power" in message bus configuration file
/var/log/syslog:Jun  4 00:42:37 nick-pc kernel: [    0.943330] usb: port power management may be unreliable
/var/log/syslog:Jun  4 00:42:37 nick-pc kernel: [    2.859650] systemd-journald[272]: File /var/log/journal/86c8e56b4e3d415cae27e07c72baa6fb/system.journal corrupted or uncleanly shut down, renaming and replacing.
/var/log/syslog:Jun  4 00:42:37 nick-pc systemd[1]: Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down.
/var/log/syslog:Jun  4 00:42:37 nick-pc NetworkManager[864]: <info>  [1559630557.4143] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, 20-connectivity-ubuntu.conf, no-mac-addr-change.conf) (run: 10-globally-managed-devices.conf) (etc: default-wifi-powersave-on.conf)
/var/log/syslog:Jun  4 00:42:37 nick-pc systemd[1]: Started Unattended Upgrades Shutdown.
/var/log/syslog:Jun  4 00:42:38 nick-pc systemd[1]: Started Daemon for power management.
/var/log/syslog:Jun  4 00:42:39 nick-pc boltd[1111]: power: force power support: yes
/var/log/syslog:Jun  4 00:42:39 nick-pc boltd[1111]: power: setting force_power to ON
/var/log/syslog:Jun  4 00:42:39 nick-pc boltd[1111]: power: guard '1' for 'boltd' active
/var/log/syslog:Jun  4 00:42:41 nick-pc kernel: [    9.165864] wlp1s0: Limiting TX power to 30 (30 - 0) dBm as advertised by cc:40:d0:05:43:fe
/var/log/syslog:Jun  4 00:42:42 nick-pc set-cpufreq[826]: Setting powersave scheduler for all CPUs
/var/log/syslog:Jun  4 00:42:44 nick-pc boltd[1111]: manager: acquired power guard '1'
/var/log/syslog:Jun  4 00:42:44 nick-pc boltd[1111]: power: guard '1' for 'boltd' deactivated
/var/log/syslog:Jun  4 00:42:44 nick-pc boltd[1111]: power: shutdown scheduled (T-20.00s)

Also, running the `last` command I can see that the system did not shut down correctly. 

Things that I have tried so far include messing with the GRUB configuration as in this thread here: [https://askubuntu.com/questions/815117/my-laptop-shuts-down-when-i-close-the-lid-even-though-its-set-to-hibernate](https://askubuntu.com/questions/815117/my-laptop-shuts-down-when-i-close-the-lid-even-though-its-set-to-hibernate)

Not sure what to do about this, but it is really frustrating since I can't suspend my laptop, I have to shut it down every time I want to move locations. As a university student this is very annoying. Any help would be extremely appreciated!

---

### Post by olivers123 on 2019-06-04
> **nickpalmer789 said:**
> Hey, I am having some weird issues with my Dell Latitude 7389 where the OS seems to crash when I close the lid after putting the computer into a suspended state. I am running Ubuntu 18.04 with the latest and greatest updates.

Specifically, this happens when I am in suspend. I tried disabling the lid close action by editing the following in /etc/systemd/logind.conf

HandleLidSwitch=ignore

And in /etc/UPower/UPower.conf:

IgnoreLid=true

Here are the interesting logs from around the time of the crash that I have found so far:
/var/log/sylog:
Jun  4 00:42:37 nick-pc systemd[1]: Starting Restore /etc/resolv.conf if the system crashed before the ppp link was shut down...Jun  4 00:42:37 nick-pc systemd[1]: Starting LSB: automatic crash report generation...
Jun  4 00:42:37 nick-pc systemd[1]: Started Restore /etc/resolv.conf if the system crashed before the ppp link [[color=#000000]gimp[/color]](https://gimp.software/) [[color=#000000]freejobalert[/color]](https://freejobalert.vip/) [[color=#000000]notepad++[/color]](https://notepad.software/) was shut down.
Jun  4 00:42:37 nick-pc apport[832]:  * Starting automatic crash report generation: apport

and 

/var/log/syslog:Jun  4 00:42:37 nick-pc dbus-daemon[844]: dbus[844]: Unknown group "power" in message bus configuration file
/var/log/syslog:Jun  4 00:42:37 nick-pc kernel: [    0.943330] usb: port power management may be unreliable
/var/log/syslog:Jun  4 00:42:37 nick-pc kernel: [    2.859650] systemd-journald[272]: File /var/log/journal/86c8e56b4e3d415cae27e07c72baa6fb/system.journal corrupted or uncleanly shut down, renaming and replacing.
/var/log/syslog:Jun  4 00:42:37 nick-pc systemd[1]: Started Restore /etc/resolv.conf if the system crashed before the ppp link was shut down.
/var/log/syslog:Jun  4 00:42:37 nick-pc NetworkManager[864]: <info>  [1559630557.4143] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, 20-connectivity-ubuntu.conf, no-mac-addr-change.conf) (run: 10-globally-managed-devices.conf) (etc: default-wifi-powersave-on.conf)
/var/log/syslog:Jun  4 00:42:37 nick-pc systemd[1]: Started Unattended Upgrades Shutdown.
/var/log/syslog:Jun  4 00:42:38 nick-pc systemd[1]: Started Daemon for power management.
/var/log/syslog:Jun  4 00:42:39 nick-pc boltd[1111]: power: force power support: yes
/var/log/syslog:Jun  4 00:42:39 nick-pc boltd[1111]: power: setting force_power to ON
/var/log/syslog:Jun  4 00:42:39 nick-pc boltd[1111]: power: guard '1' for 'boltd' active
/var/log/syslog:Jun  4 00:42:41 nick-pc kernel: [    9.165864] wlp1s0: Limiting TX power to 30 (30 - 0) dBm as advertised by cc:40:d0:05:43:fe
/var/log/syslog:Jun  4 00:42:42 nick-pc set-cpufreq[826]: Setting powersave scheduler for all CPUs
/var/log/syslog:Jun  4 00:42:44 nick-pc boltd[1111]: manager: acquired power guard '1'
/var/log/syslog:Jun  4 00:42:44 nick-pc boltd[1111]: power: guard '1' for 'boltd' deactivated
/var/log/syslog:Jun  4 00:42:44 nick-pc boltd[1111]: power: shutdown scheduled (T-20.00s)

Also, running the `last` command I can see that the system did not shut down correctly. 

Things that I have tried so far include messing with the GRUB configuration as in this thread here: [https://askubuntu.com/questions/815117/my-laptop-shuts-down-when-i-close-the-lid-even-though-its-set-to-hibernate](https://askubuntu.com/questions/815117/my-laptop-shuts-down-when-i-close-the-lid-even-though-its-set-to-hibernate)

Not sure what to do about this, but it is really frustrating since I can't suspend my laptop, I have to shut it down every time I want to move locations. As a university student this is very annoying. Any help would be extremely appreciated!
Facing the same issues here too. In need of help ASAP.

THanks in advance.
Regards,
Oliver

---

