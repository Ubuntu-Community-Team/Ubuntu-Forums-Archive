---
title: "long boot time apt-daily.service 4 minutes."
date: 2016-09-19
forum: General Help
---

### Post by cain071546 on 2016-09-19
Long initial boot times in the morning.

systemd-analyze blame outputs

```
4min 53.597s apt-daily.service
         12.523s NetworkManager.service
          8.856s ModemManager.service
          8.373s dev-sdc1.device
          6.213s apparmor.service
          6.194s accounts-daemon.service
          5.678s systemd-tmpfiles-setup.service
          5.361s snapd.firstboot.service
          5.033s thermald.service
          4.552s lightdm.service
          4.441s gpu-manager.service
          3.336s grub-common.service
          3.144s rsyslog.service
          2.660s irqbalance.service
          2.622s systemd-fsck@dev-disk-by\x2duuid-477747ce\x2d1695\x2d468f\x2d91
          2.410s avahi-daemon.service
          2.017s console-setup.service
          1.886s keyboard-setup.service
          1.883s systemd-udevd.service
          1.793s apport.service
          1.732s plymouth-start.service
          1.728s systemd-tmpfiles-setup-dev.service
          1.560s networking.service


```

---

### Post by #&amp;thj^% on 2016-09-19
What dose this show from the terminal
```
systemctl list-units --type service --all
```
Might be easier to find the culprit.

---

### Post by cain071546 on 2016-09-19
```
 UNIT                       LOAD      ACTIVE   SUB     DESCRIPTION
  accounts-daemon.service    loaded    active   running Accounts Service
  acpid.service              loaded    active   running ACPI event daemon
  alsa-restore.service       loaded    active   exited  Save/Restore Sound Card 
  alsa-state.service         loaded    inactive dead    Manage Sound Card State 
  anacron.service            loaded    inactive dead    Run anacron jobs
  apparmor.service           loaded    active   exited  LSB: AppArmor initializa
  apport.service             loaded    active   exited  LSB: automatic crash rep
  apt-daily.service          loaded    inactive dead    Daily apt activities
&#9679; auditd.service             not-found inactive dead    auditd.service
  avahi-daemon.service       loaded    active   running Avahi mDNS/DNS-SD Stack
  brltty.service             loaded    inactive dead    Braille Device Support
&#9679; cloud-init.service         not-found inactive dead    cloud-init.service
  colord.service             loaded    active   running Manage, Install and Gene
&#9679; console-screen.service     not-found inactive dead    console-screen.service
  console-setup.service      loaded    active   exited  Set console font and key
  cron.service               loaded    active   running Regular background progr
  cups-browsed.service       loaded    active   running Make remote CUPS printer
  cups.service               loaded    inactive dead    CUPS Scheduler
  dbus.service               loaded    active   running D-Bus System Message Bus
  dns-clean.service          loaded    inactive dead    Clean up any mess left b
  emergency.service          loaded    inactive dead    Emergency Shell
  failsafe-x.service         loaded    inactive dead    X.org diagnosis failsafe


```

---

### Post by #&amp;thj^% on 2016-09-19
> **cain071546 said:**
> ```
 UNIT                       LOAD      ACTIVE   SUB     DESCRIPTION
  accounts-daemon.service    loaded    active   running Accounts Service
  acpid.service              loaded    active   running ACPI event daemon
  alsa-restore.service       loaded    active   exited  Save/Restore Sound Card 
  alsa-state.service         loaded    inactive dead    Manage Sound Card State 
  anacron.service            loaded    inactive dead    Run anacron jobs
  apparmor.service           loaded    active   exited  LSB: AppArmor initializa
  apport.service             loaded    active   exited  LSB: automatic crash rep
  apt-daily.service          loaded    inactive dead    Daily apt activities
&#9679; auditd.service             not-found inactive dead    auditd.service
  avahi-daemon.service       loaded    active   running Avahi mDNS/DNS-SD Stack
  brltty.service             loaded    inactive dead    Braille Device Support
&#9679; cloud-init.service         not-found inactive dead    cloud-init.service
  colord.service             loaded    active   running Manage, Install and Gene
&#9679; console-screen.service     not-found inactive dead    console-screen.service
  console-setup.service      loaded    active   exited  Set console font and key
  cron.service               loaded    active   running Regular background progr
  cups-browsed.service       loaded    active   running Make remote CUPS printer
  cups.service               loaded    inactive dead    CUPS Scheduler
  dbus.service               loaded    active   running D-Bus System Message Bus
  dns-clean.service          loaded    inactive dead    Clean up any mess left b
  emergency.service          loaded    inactive dead    Emergency Shell
  failsafe-x.service         loaded    inactive dead    X.org diagnosis failsafe


```
Well I was wrong...that was not that helpful after all':)
Not sure what is hanging up "apt-daily.service" That a new one for me.
If this bothers you greatly you can adjust systemd time out period by editing the "/etc/systemd/system.conf" file.
I always have thought that 90 Secs was to long to wait.
 issue these commands as an example of how to edit /etc/systemd/system.conf
```
sudo cp /etc/systemd/system.conf /etc/systemd/system.conf.bu
```
That will make a back-up for safety.
```
gksudo <your favorite text editor here> /etc/systemd/system.conf
```
Look for and change these 2 lines
```
#DefaultTimeoutStartSec=90s
#DefaultTimeoutStopSec=90s

```
Mine now look like this
```
DefaultTimeoutStartSec=10s
DefaultTimeoutStopSec=10s
```
Been doing that for year now and nothing bad has come of it.

---

