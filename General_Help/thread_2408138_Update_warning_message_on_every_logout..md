---
title: "Update warning message on every logout."
date: 2018-12-14
forum: General Help
---

### Post by maglin2 on 2018-12-14
Every time I try to logout I see the following message in the logout dialogue box:

'Are you sure you want to close all programs and log out?
 Some software updates won't be applied until the computer next restarts'

This message persists if I try to log out immediately after reboot and login.

I also note in System Monitor that 'unattended-upgrade-shutdown' process starts up at boot. The tooltip message is '--wait-for-signal'

I have tried:
sudo dpkg --configure -asudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean

all without effect.

Synaptic shows no broken packages and none to install/upgrade.

My concern is that there may be an incomplete update lurking somewhere in apt, or that apt is borked.
Any advice on how to determine if this is the case appreciated.

Running 18.04 gnome session flashback. If I use standard ubuntu session there is no logout warning message, but 'unattended-upgrade-shutdown' process still starts up at boot.

Thanks

---

### Post by Claus7 on 2019-02-08
Hello,

as it seems you to not provide enough time to your system to start prior to shutting it down. Commands like:
systemd-analyze blame
systemd-analyze time

will give you an insight about the boot time of your system. If they provide no output when issued, it means that your system is not "ready" yet, or boot is not finished. If you have hdd instead of sdd this is going to be even more prominent.

Regards!

---

