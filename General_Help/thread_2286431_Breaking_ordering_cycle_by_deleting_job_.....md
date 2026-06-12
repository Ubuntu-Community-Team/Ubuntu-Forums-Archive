---
title: "Breaking ordering cycle by deleting job ...."
date: 2015-07-12
forum: General Help
---

### Post by lister171254 on 2015-07-12
I've upgraded to 15.04 and am investigating why shorewall doesn't start automatically after a boot. 

Lokking at syslog I found that shorewall (and other jobs are being stopped)

```
Jul 12 11:11:58 LeosGameLaptop kernel: [   27.062936] systemd[1]: Breaking ordering cycle by deleting job dbus.socket/start
Jul 12 11:11:58 LeosGameLaptop kernel: [   27.063034] systemd[1]: Breaking ordering cycle by deleting job acpid.socket/start
Jul 12 11:11:58 LeosGameLaptop kernel: [   27.063085] systemd[1]: Breaking ordering cycle by deleting job cups.socket/start
Jul 12 11:11:58 LeosGameLaptop kernel: [   27.063133] systemd[1]: Breaking ordering cycle by deleting job avahi-daemon.socket/start
Jul 12 11:11:58 LeosGameLaptop kernel: [   27.063182] systemd[1]: Breaking ordering cycle by deleting job uuidd.socket/start
Jul 12 11:11:58 LeosGameLaptop kernel: [   27.063229] systemd[1]: Breaking ordering cycle by deleting job paths.target/start
Jul 12 11:11:58 LeosGameLaptop kernel: [   27.063274] systemd[1]: Breaking ordering cycle by deleting job shorewall.service/start

```

I'd appreciate any hints as to how this can be fixed

---

