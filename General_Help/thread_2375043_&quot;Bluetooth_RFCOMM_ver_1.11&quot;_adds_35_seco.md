---
title: "&quot;Bluetooth: RFCOMM ver 1.11&quot; adds 35 seconds to boot time"
date: 2017-10-21
forum: General Help
---

### Post by RavanH on 2017-10-21
Hi all,

I noticed boot time on Ubuntu 17.10 (clean install) takes considerably longer than my previous Ubuntu GNOME 17.04. I timed around 56 seconds before GDM login screen where 17.04 (also using GDM) usually took about 34 seconds.

Looking at the system boot log, I notice a very long time is taken by only the last 5 entries. See the end of this (complete) dmesg output on [https://paste.ubuntu.com/25785631/](https://paste.ubuntu.com/25785631/) 

Why are these last few steps taking so long? 35 seconds for Bluetooth? I don't even use it that much :(

Is this a driver bug or a hardware problem? Is anyone else suffering this issue?

Thanks for any thoughts :)

---

### Post by jeremy31 on 2017-10-21
Try ```
systemd-analyze blame > blame.txt
```
See what the blame.txt file says is taking the time

---

### Post by RavanH on 2017-10-22
Hi @jeremy31 thanks, that's an interesting command :)

Here's my blame.txt [https://paste.ubuntu.com/25798636/](https://paste.ubuntu.com/25798636/) 

Question: is snapd installed and running by default or did it come along when I installed a snap package?

---

### Post by jeremy31 on 2017-10-27
```
28.515s apt-daily.service
```
You could change the update settings to check for update every 3 days and see if it boots quicker.  I am not sure why plymouth-quit-wait.service takes 27 seconds

---

### Post by RavanH on 2017-11-03
Hi @jeremy31 thanks for your thoughts :)

I tried weekly instead of daily but it does not even take one second off... Any way to inspect plymouth-quit-wait.service ?

---

### Post by jeremy31 on 2017-11-03
You might be able to disable it as I think plymouth is just the splash image during boot and shutdown

---

### Post by RavanH on 2017-11-06
Removed plymouth splash with ```
sudo apt remove plymouth-theme-*
``` and plymouth-quit-wait.service disappeared from the systemd-analyze blame list but boot time to GDM login screen remains unchanged, around 56 seconds...

```
$ systemd-analyze blame
          9.637s ModemManager.service
          7.334s NetworkManager-wait-online.service
          7.326s networking.service
          6.327s dev-sda8.device
          5.991s NetworkManager.service
          5.160s grub-common.service
          4.779s accounts-daemon.service
          4.650s gpu-manager.service
          4.639s fwupd.service
          4.256s udisks2.service
          4.086s rsyslog.service
          3.353s polkit.service
          2.736s systemd-fsck@dev-disk-by\x2duuid-A0A2\x2dEA36.service
          2.546s thermald.service
          2.308s postfix@-.service
          2.256s php7.1-fpm.service
          2.166s apparmor.service
          1.554s systemd-fsck@dev-disk-by\x2duuid-7da2ba7b\x2d0259\x2d466d\x2dbe
          1.438s apport.service
          1.405s gdm.service
          1.334s avahi-daemon.service
          1.233s home.mount
          1.151s dns-clean.service
...

```

---

