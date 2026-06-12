---
title: "Improve start time"
date: 2017-06-09
forum: General Help
---

### Post by csdgbas on 2017-06-09
I'm trying to improve the amount of time it takes to start Ubuntu on my computer.  It seems (from systemd-analyze blame) that the following are the worst culprits:

14.072s keyboard-setup.service      (why does this take so long?)
13.798s dev-sda8.device      (guessing there isn't much I can do about this - the hard drive takes as long as the hard drive takes)
10.413s systemd-tmpfiles-setup-dev.service
9.559s NetworkManager-wait-online.service
6.028s click-system-hooks.service

---

### Post by HermanAB on 2017-06-09
The best way to improve the start time, is to avoid restarting in the first place.  Suspend, don't restart.  

A Linux machine can run for years without ever restarting.

---

### Post by csdgbas on 2017-06-10
> **HermanAB said:**
> Suspend, don't restart.

Actually, I'll decide what I do with my computer.

---

### Post by Autodave on 2017-06-10
You asked for suggestions, he merely gave you one. Keep in mind that everyone here does this voluntarily: no paid positions.

---

### Post by missmoondog on 2017-06-10
never really thought about this, but i know my linux computers start much faster than any windows computers! :)

---

### Post by fyfe54 on 2017-06-10
Use an SSD?  My laptop boots decrypts and boots to a working, logged-in  system in 30 seconds.

---

### Post by Autodave on 2017-06-10
Same computer: boot to Win 10 (with fast boot off) takes a little over a minute. Xubuntu 16.04 takes 20 seconds.

---

### Post by vasa1 on 2017-06-10
> **Autodave said:**
> You asked for suggestions, he merely gave you one. Keep in mind that everyone here does this voluntarily: no paid positions.
+1

From the Forum Rules:> The purpose of the Ubuntu Forums is to provide support for Ubuntu. We also want this to be a place where community can develop and we can enjoy one another's company. To achieve this, we strive to maintain an atmosphere that can be enjoyed by all and we ask all members of the community to be respectful at all times. This means please use etiquette and politeness. Treat people with respect. If you do this, the rest of the code of conduct won't need more than a cursory mention.

---

### Post by csdgbas on 2017-06-10
> **Autodave said:**
> You asked for suggestions, he merely gave you one. Keep in mind that everyone here does this voluntarily: no paid positions.

A suggestion which is utterly meaningless in the context he has.  In other words, a guess.  I actually *gave* the context needed in the lines detailing which services have been measured to take the most time.

---

### Post by QIII on 2017-06-10
Hello!

Please don't make demands or set conditions on the sort of answers you get from the volunteers who populate the forums.  If you don't like an answer, you may: ignore it and wait for a better one; or add more information if you realize you did not include enough in your first post.  Snide responses are not likely to encourage others to help.

Cheers!

---

### Post by him610 on 2017-06-10
With solid state drive, this is what I get
```
$ systemd-analyze blame
         19.394s apt-daily.service
          7.149s NetworkManager-wait-online.service
          1.254s dev-sda1.device
           736ms lvm2-monitor.service
           603ms lxd-containers.service
           475ms NetworkManager.service
           401ms ModemManager.service
           401ms accounts-daemon.service
           389ms upower.service
           282ms grub-common.service
           272ms networking.service
           239ms gpu-manager.service
           206ms systemd-fsck@dev-disk-by\x2duuid-dc8ad078\x2d8577\x2d42a4\x2d85b9\x2dd682be1e574f.s
           200ms console-setup.service
           193ms mdadm.service
           190ms keyboard-setup.service
           187ms systemd-logind.service
           170ms avahi-daemon.service
           166ms apparmor.service
           166ms systemd-modules-load.service
           138ms systemd-journald.service
           137ms systemd-udev-trigger.service
           134ms colord.service
           133ms systemd-rfkill.service
           106ms lightdm.service
            89ms ondemand.service
            87ms irqbalance.service
            85ms plymouth-quit-wait.service
            83ms lm-sensors.service
...
            12ms setvtrgb.service
             9ms systemd-user-sessions.service
             8ms rtkit-daemon.service
             8ms lxd.socket
             7ms ureadahead-stop.service
             7ms sys-fs-fuse-connections.mount
             7ms systemd-remount-fs.service
             5ms systemd-random-seed.service
             5ms snapd.socket
             4ms rc-local.service
 
```

OS installed on /dev/sda (SSD), /home resides on /dev/sdb (HDD)
```
inxi -D
Drives:    HDD Total Size: 531.8GB (6.3% used) ID-1: /dev/sda model: KingDian_S100_32 size: 31.7GB
           ID-2: /dev/sdb model: WDC_WD5000AAKX size: 500.1GB

```

---

