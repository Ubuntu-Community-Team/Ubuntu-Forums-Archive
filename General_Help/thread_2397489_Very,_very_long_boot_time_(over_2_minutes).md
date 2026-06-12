---
title: "Very, very long boot time (over 2 minutes)"
date: 2018-07-30
forum: General Help
---

### Post by neepox on 2018-07-30
Hello. I freshly installed Ubuntu 18.04 (with LLVM) on my desktop PC and I'm experiencing very long boot times. Yes, it's well over 1.5 minutes, sometimes 2. That is really strange and I don't know why, neither I don't know how to find out why. Specs of my PC are: overclocked AMD FX 6300, 8GB of RAM, 1TB Seagate HDD, Nvidia Geforce GT 760 using proprietary drivers. Thing is, this machine has had Windows 10 booting around 20 seconds and Ubuntu 18.04 booting around 40 seconds and I thought that was long because back then I used Full disc encryption. Now it has none and it's waaaay slower.

Posting systemd-analyze blame command:

```
10.039s dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
          9.123s keyboard-setup.service
          9.093s systemd-localed.service
          8.536s systemd-journal-flush.service
          7.186s plymouth-quit-wait.service
          7.069s NetworkManager-wait-online.service
          6.989s udisks2.service
          6.725s bolt.service
          6.377s snapd.service
          6.306s networkd-dispatcher.service
          6.254s grub-common.service
          5.338s NetworkManager.service
          5.297s ModemManager.service
          4.989s wpa_supplicant.service
          4.546s accounts-daemon.service
          3.411s rsyslog.service
          2.856s bluetooth.service
          2.688s avahi-daemon.service
          2.630s apparmor.service
          2.535s polkit.service
          2.417s colord.service
          2.351s apport.service
          2.290s thermald.service

```

Don't know what am I doing wrong. Help is appreciated.

---

### Post by mIk3_08 on 2018-07-30
try to update grub; Open your terminal
ctrl + alt + t
Then type the command
```
sudo update-grub
```


Reboot the computer

---

### Post by monkeybrain20122 on 2018-07-30
It may be this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1779961")  in kernel 4.15.0-24. You can check by booting into kernel 4.15.0-23  (press esc or shift when boot to see the grub screen, choose advanced  options and choose the older kernel) and see if it still takes that  long.

If confirm it is the bad kernel, see post 14 in[ this thread]("https://ubuntuforums.org/showthread.php?t=2395459&page=2") for the simple workaround.

---

### Post by oldfred on 2018-07-30
What motherboard?
Some require boot parameters.

Are you using snaps? but your may only save the 6.7 sec?
       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)

Check that all UUIDs in fstab match valid UUIDs. Some users have newer swap partition or other obsolete mount and it has to time out.
lsblk -f
cat /etc/fstab

Are drives set for AHCI? Windows needs AHCI drivers before changing in UEFI.

---

