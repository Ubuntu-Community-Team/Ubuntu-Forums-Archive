---
title: "Ubuntu pro - unable to set up livepatch"
date: 2023-02-18
forum: General Help
---

### Post by Anquietas on 2023-02-18
Hello,

I have generated a "Free for personal use" token for Ubuntu Pro.

I have 3 machines. On 2 of them, everything works smoothly.

On one of them, I have the following problem:

```

infosky [~] # pro status
SERVICE          ENTITLED  STATUS    DESCRIPTION
esm-apps         yes       enabled   Expanded Security Maintenance for Applications
esm-infra        yes       enabled   Expanded Security Maintenance for Infrastructure
livepatch        yes       disabled  Canonical Livepatch service
realtime-kernel  yes       disabled  Ubuntu kernel with PREEMPT_RT patches integrated

Enable services with: pro enable <service>

     Account: XXX
Subscription: Ubuntu Pro - free personal subscription
infosky [~] # pro enable livepatch
One moment, checking your subscription first
Installing canonical-livepatch snap
Stderr: error: cannot perform the following tasks:
- Run hook connect-plug-etc-update-motd-d of snap "canonical-livepatch" (run hook "connect-plug-etc-update-motd-d": cannot perform operation: mount --rbind /home /tmp/snap.rootfs_0yphi5//home: Permission denied)


Stderr: error: cannot perform the following tasks:
- Run hook connect-plug-etc-update-motd-d of snap "canonical-livepatch" (run hook "connect-plug-etc-update-motd-d": cannot perform operation: mount --rbind /home /tmp/snap.rootfs_HLNHbo//home: Permission denied)


Stderr: error: cannot perform the following tasks:
- Run hook connect-plug-etc-update-motd-d of snap "canonical-livepatch" (run hook "connect-plug-etc-update-motd-d": cannot perform operation: mount --rbind /home /tmp/snap.rootfs_79xi20//home: Permission denied)


Stderr: error: cannot perform the following tasks:
- Run hook connect-plug-etc-update-motd-d of snap "canonical-livepatch" (run hook "connect-plug-etc-update-motd-d": cannot perform operation: mount --rbind /home /tmp/snap.rootfs_zaO8uo//home: Permission denied)


Unable to install Livepatch client: Failed running command '/usr/bin/snap install canonical-livepatch' [exit(1)]. Message: error: cannot perform the following tasks:
- Run hook connect-plug-etc-update-motd-d of snap "canonical-livepatch" (run hook "connect-plug-etc-update-motd-d": cannot perform operation: mount --rbind /home /tmp/snap.rootfs_zaO8uo//home: Permission denied)

infosky [~] # snap refresh
All snaps up to date.
infosky [~] # snap refresh core
snap "core" has no updates available
infosky [~] # snap install core
snap "core" is already installed, see 'snap help refresh'
infosky [~] # ll /home
lrwxrwxrwx 1 root root 9 Nov 11  2020 /home -> /srv/home/

infosky [~] # snap install canonical-livepatch
error: cannot perform the following tasks:
- Run hook connect-plug-etc-update-motd-d of snap "canonical-livepatch" (run hook "connect-plug-etc-update-motd-d": cannot perform operation: mount --rbind /home /tmp/snap.rootfs_h2YPfe//home: Permission denied)
infosky [~] #

```

Ubuntu Server 22.04.1 LTS
Kernel: 5.15.0-60-generic

Any help would be great ! :-)
Thank you !

---

### Post by MAFoElffen on 2023-02-18
What "IS" the machine in question? Arch, make and model? OS version and Type (Server/Desktop)

---

### Post by Anquietas on 2023-02-19
It's a Desktop PC used as a Server.

Lenovo ThinkCentre M92P

Intel ® Core(TM) i5-3470 CPU
3.2 GHz
64 Bit
4 cores

8 GB of DDR3 RAM

Ubuntu Server 22.04.1 LTS
Kernel: 5.15.0-60-generic

---

### Post by MAFoElffen on 2023-02-19
I don't see a problem with compatibility there...

When i did my tests for Ubuntu Pro Subscriptions... I got live support for that from Chat Feature by selecting the little chat icon on the lower right of the page at: [https://ubuntu.com/pro/subscribe](https://ubuntu.com/pro/subscribe) 

You might try that to see if they can figure out why that is not working for you... They can access your Ubuntu Pro account and see what is going on with that.

Please post back when if they can figure that out for you, to help others with similar problems

---

