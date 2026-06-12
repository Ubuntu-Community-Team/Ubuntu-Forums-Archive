---
title: "can't properly shutdown laptop"
date: 2013-02-25
forum: General Help
---

### Post by greythorne on 2013-02-25
installed ubuntu 12.10 64bit on hp dm4 laptop. now after update and using the latest kernel I can't properly shutdown. have to press the button to shutdown. 

any help on this?

thank you.

---

### Post by dino99 on 2013-02-25
youy will get more details by removing "quiet splash" from /etc/default/grub, then: sudo update-grub

---

### Post by greythorne on 2013-02-25
> **dino99 said:**
> youy will get more details by removing "quiet splash" from /etc/default/grub, then: sudo update-grub

This is what I observed. 
snip

Can tell me what to do?

---

### Post by matt_symes on 2013-02-25
Hii

If you open a terminal and type

```
sudo shutdown -h now
```

Does that shut the laptop down ?

Kind regards

---

### Post by greythorne on 2013-02-25
> **matt_symes said:**
> Hii

If you open a terminal and type

```
sudo shutdown -h now
```

Does that shut the laptop down ?

Kind regards

Yup I tried that but didn't work. Shuts down halfway after that I will have to force shutdown by pressing the button on my laptop.

---

### Post by matt_symes on 2013-02-26
Hi

If you boot into the old kernel does it shutdown again ?

This will eliminate/implicate the kernel or other updates as the cause.

Kind regards

---

### Post by greythorne on 2013-02-26
> **matt_symes said:**
> Hi

If you boot into the old kernel does it shutdown again ?

This will eliminate/implicate the kernel or other updates as the cause.

Kind regards

Ok tried using the old kernel however my laptop never shutdown. I still see the message in the attached image.

Do I reinstall? Also why am i  unable to install Ati drivers?

---

### Post by bantuvez on 2013-02-26
You might try 

```
sudo poweroff
```

---

### Post by matt_symes on 2013-02-26
Hi

Let's cover one issue at a time.

That may discount the kernel if you cant shutdown with the old kernel.

ieee80211 relates to wireless networks and you may have had an update to the wireless subsystem.

Open a terminal and type

```
sudo lshw -c network
```

Post the back here.

Also copy and paste this into the terminal

```
grep " installed" dpkg.log | egrep "2013-02-26|2013-02-25|2013-02-24"
```

Post back results

Kind regards

---

### Post by greythorne on 2013-02-27
> **matt_symes said:**
> Hi

Let's cover one issue at a time.

That may discount the kernel if you cant shutdown with the old kernel.

ieee80211 relates to wireless networks and you may have had an update to the wireless subsystem.

Open a terminal and type

```
sudo lshw -c network
```Post the back here.

Also copy and paste this into the terminal

```
grep " installed" dpkg.log | egrep "2013-02-26|2013-02-25|2013-02-24"
```Post back results

Kind regards

Form ```
sudo lshw -c network
```> *-network              
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 1c:c1:de:a0:0b:b4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:c2400000-c2403fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:f3:95:34:f1:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.5.0-25-generic firmware=N/A ip=192.168.0.199 link=yes multicast=yes wireless=IEEE 802.11bgnOk for the ```
grep " installed" dpkg.log | egrep "2013-02-26|2013-02-25|2013-02-24"
```> grep: dpkg.log: No such file or directoryLet me know what else i should provide.

Thank you.

Regards

---

### Post by matt_symes on 2013-02-27
Hi

Sorry that should have been

```
grep " installed" /var/log/dpkg.log | egrep "2013-02-26|2013-02-25|2013-02-24"
```

Can you post that back please.

I suspect that something in your wireless subsystem is causing your system to hang and i want to see if you had a recent update for it.

Kind regards

---

### Post by greythorne on 2013-03-02
> **matt_symes said:**
> Hi

Sorry that should have been

```
grep " installed" /var/log/dpkg.log | egrep "2013-02-26|2013-02-25|2013-02-24"
```

Can you post that back please.

I suspect that something in your wireless subsystem is causing your system to hang and i want to see if you had a recent update for it.

Kind regards

> 2013-03-01 14:14:56 startup archives unpack
2013-03-01 14:14:59 upgrade libssl1.0.0:amd64 1.0.1c-3ubuntu2.1 1.0.1c-3ubuntu2.2
2013-03-01 14:14:59 status half-configured libssl1.0.0:amd64 1.0.1c-3ubuntu2.1
2013-03-01 14:14:59 status unpacked libssl1.0.0:amd64 1.0.1c-3ubuntu2.1
2013-03-01 14:14:59 status half-installed libssl1.0.0:amd64 1.0.1c-3ubuntu2.1
2013-03-01 14:14:59 status half-installed libssl1.0.0:amd64 1.0.1c-3ubuntu2.1
2013-03-01 14:14:59 status unpacked libssl1.0.0:amd64 1.0.1c-3ubuntu2.2
2013-03-01 14:14:59 status unpacked libssl1.0.0:amd64 1.0.1c-3ubuntu2.2
2013-03-01 14:15:00 upgrade libdbus-glib-1-2:amd64 0.100-1 0.100-1ubuntu0.1
2013-03-01 14:15:00 status half-configured libdbus-glib-1-2:amd64 0.100-1
2013-03-01 14:15:00 status unpacked libdbus-glib-1-2:amd64 0.100-1
2013-03-01 14:15:00 status half-installed libdbus-glib-1-2:amd64 0.100-1
2013-03-01 14:15:00 status half-installed libdbus-glib-1-2:amd64 0.100-1
2013-03-01 14:15:00 status unpacked libdbus-glib-1-2:amd64 0.100-1ubuntu0.1
2013-03-01 14:15:00 status unpacked libdbus-glib-1-2:amd64 0.100-1ubuntu0.1
2013-03-01 14:15:01 upgrade sudo:amd64 1.8.5p2-1ubuntu1 1.8.5p2-1ubuntu1.1
2013-03-01 14:15:01 status half-configured sudo:amd64 1.8.5p2-1ubuntu1
2013-03-01 14:15:01 status unpacked sudo:amd64 1.8.5p2-1ubuntu1
2013-03-01 14:15:01 status half-installed sudo:amd64 1.8.5p2-1ubuntu1
2013-03-01 14:15:01 status triggers-pending ureadahead:amd64 0.100.0-12build1
2013-03-01 14:15:01 status half-installed sudo:amd64 1.8.5p2-1ubuntu1
2013-03-01 14:15:01 status triggers-pending man-db:amd64 2.6.3-1
2013-03-01 14:15:01 status half-installed sudo:amd64 1.8.5p2-1ubuntu1
2013-03-01 14:15:01 status half-installed sudo:amd64 1.8.5p2-1ubuntu1
2013-03-01 14:15:01 status unpacked sudo:amd64 1.8.5p2-1ubuntu1.1
2013-03-01 14:15:01 status unpacked sudo:amd64 1.8.5p2-1ubuntu1.1
2013-03-01 14:15:02 upgrade openssl:amd64 1.0.1c-3ubuntu2.1 1.0.1c-3ubuntu2.2
2013-03-01 14:15:02 status half-configured openssl:amd64 1.0.1c-3ubuntu2.1
2013-03-01 14:15:02 status unpacked openssl:amd64 1.0.1c-3ubuntu2.1
2013-03-01 14:15:02 status half-installed openssl:amd64 1.0.1c-3ubuntu2.1
2013-03-01 14:15:02 status half-installed openssl:amd64 1.0.1c-3ubuntu2.1
2013-03-01 14:15:03 status half-installed openssl:amd64 1.0.1c-3ubuntu2.1
2013-03-01 14:15:03 status unpacked openssl:amd64 1.0.1c-3ubuntu2.2
2013-03-01 14:15:03 status unpacked openssl:amd64 1.0.1c-3ubuntu2.2
2013-03-01 14:15:03 upgrade boot-sav:all 3.197~ppa33~quantal 3.197~ppa34~quantal
2013-03-01 14:15:03 status half-configured boot-sav:all 3.197~ppa33~quantal
2013-03-01 14:15:03 status unpacked boot-sav:all 3.197~ppa33~quantal
2013-03-01 14:15:03 status half-installed boot-sav:all 3.197~ppa33~quantal
2013-03-01 14:15:04 status half-installed boot-sav:all 3.197~ppa33~quantal
2013-03-01 14:15:04 status unpacked boot-sav:all 3.197~ppa34~quantal
2013-03-01 14:15:04 status unpacked boot-sav:all 3.197~ppa34~quantal
2013-03-01 14:15:04 upgrade boot-repair:all 3.197~ppa33~quantal 3.197~ppa34~quantal
2013-03-01 14:15:04 status half-configured boot-repair:all 3.197~ppa33~quantal
2013-03-01 14:15:04 status unpacked boot-repair:all 3.197~ppa33~quantal
2013-03-01 14:15:04 status half-installed boot-repair:all 3.197~ppa33~quantal
2013-03-01 14:15:04 status triggers-pending bamfdaemon:amd64 0.3.4-0ubuntu1
2013-03-01 14:15:04 status half-installed boot-repair:all 3.197~ppa33~quantal
2013-03-01 14:15:04 status triggers-pending desktop-file-utils:amd64 0.20-0.1ubuntu1
2013-03-01 14:15:04 status half-installed boot-repair:all 3.197~ppa33~quantal
2013-03-01 14:15:04 status triggers-pending gnome-menus:amd64 3.6.0-0ubuntu1
2013-03-01 14:15:04 status half-installed boot-repair:all 3.197~ppa33~quantal
2013-03-01 14:15:05 status half-installed boot-repair:all 3.197~ppa33~quantal
2013-03-01 14:15:05 status half-installed boot-repair:all 3.197~ppa33~quantal
2013-03-01 14:15:05 status unpacked boot-repair:all 3.197~ppa34~quantal
2013-03-01 14:15:05 status unpacked boot-repair:all 3.197~ppa34~quantal
2013-03-01 14:15:05 upgrade boot-sav-extra:all 3.197~ppa33~quantal 3.197~ppa34~quantal
2013-03-01 14:15:05 status half-configured boot-sav-extra:all 3.197~ppa33~quantal
2013-03-01 14:15:05 status unpacked boot-sav-extra:all 3.197~ppa33~quantal
2013-03-01 14:15:05 status half-installed boot-sav-extra:all 3.197~ppa33~quantal
2013-03-01 14:15:05 status half-installed boot-sav-extra:all 3.197~ppa33~quantal
2013-03-01 14:15:05 status unpacked boot-sav-extra:all 3.197~ppa34~quantal
2013-03-01 14:15:05 status unpacked boot-sav-extra:all 3.197~ppa34~quantal
2013-03-01 14:15:06 upgrade firefox-globalmenu:amd64 19.0+build1-0ubuntu0.12.10.1 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:06 status half-configured firefox-globalmenu:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:06 status unpacked firefox-globalmenu:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:06 status half-installed firefox-globalmenu:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:06 status half-installed firefox-globalmenu:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:06 status unpacked firefox-globalmenu:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:06 status unpacked firefox-globalmenu:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:07 upgrade firefox:amd64 19.0+build1-0ubuntu0.12.10.1 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:07 status half-configured firefox:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:07 status unpacked firefox:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:07 status half-installed firefox:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:07 status half-installed firefox:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:08 status half-installed firefox:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:08 status half-installed firefox:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:08 status half-installed firefox:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:08 status half-installed firefox:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:08 status unpacked firefox:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:08 status unpacked firefox:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:08 upgrade firefox-gnome-support:amd64 19.0+build1-0ubuntu0.12.10.1 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:08 status half-configured firefox-gnome-support:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:08 status unpacked firefox-gnome-support:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:09 status half-installed firefox-gnome-support:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:09 status half-installed firefox-gnome-support:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:09 status unpacked firefox-gnome-support:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:09 status unpacked firefox-gnome-support:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:09 upgrade firefox-locale-en:amd64 19.0+build1-0ubuntu0.12.10.1 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:09 status half-configured firefox-locale-en:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:09 status unpacked firefox-locale-en:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:09 status half-installed firefox-locale-en:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:09 status half-installed firefox-locale-en:amd64 19.0+build1-0ubuntu0.12.10.1
2013-03-01 14:15:10 status unpacked firefox-locale-en:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:10 status unpacked firefox-locale-en:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:10 trigproc ureadahead:amd64 0.100.0-12build1 0.100.0-12build1
2013-03-01 14:15:10 status half-configured ureadahead:amd64 0.100.0-12build1
2013-03-01 14:15:10 status installed ureadahead:amd64 0.100.0-12build1
2013-03-01 14:15:10 trigproc man-db:amd64 2.6.3-1 2.6.3-1
2013-03-01 14:15:10 status half-configured man-db:amd64 2.6.3-1
2013-03-01 14:15:12 status installed man-db:amd64 2.6.3-1
2013-03-01 14:15:12 trigproc bamfdaemon:amd64 0.3.4-0ubuntu1 0.3.4-0ubuntu1
2013-03-01 14:15:12 status half-configured bamfdaemon:amd64 0.3.4-0ubuntu1
2013-03-01 14:15:12 status installed bamfdaemon:amd64 0.3.4-0ubuntu1
2013-03-01 14:15:12 trigproc desktop-file-utils:amd64 0.20-0.1ubuntu1 0.20-0.1ubuntu1
2013-03-01 14:15:12 status half-configured desktop-file-utils:amd64 0.20-0.1ubuntu1
2013-03-01 14:15:12 status installed desktop-file-utils:amd64 0.20-0.1ubuntu1
2013-03-01 14:15:12 trigproc gnome-menus:amd64 3.6.0-0ubuntu1 3.6.0-0ubuntu1
2013-03-01 14:15:12 status half-configured gnome-menus:amd64 3.6.0-0ubuntu1
2013-03-01 14:15:12 status installed gnome-menus:amd64 3.6.0-0ubuntu1
2013-03-01 14:15:13 startup packages configure
2013-03-01 14:15:13 configure libssl1.0.0:amd64 1.0.1c-3ubuntu2.2 <none>
2013-03-01 14:15:13 status unpacked libssl1.0.0:amd64 1.0.1c-3ubuntu2.2
2013-03-01 14:15:13 status half-configured libssl1.0.0:amd64 1.0.1c-3ubuntu2.2
2013-03-01 14:15:13 status installed libssl1.0.0:amd64 1.0.1c-3ubuntu2.2
2013-03-01 14:15:13 status triggers-pending libc-bin:amd64 2.15-0ubuntu20
2013-03-01 14:15:14 configure libdbus-glib-1-2:amd64 0.100-1ubuntu0.1 <none>
2013-03-01 14:15:14 status unpacked libdbus-glib-1-2:amd64 0.100-1ubuntu0.1
2013-03-01 14:15:14 status half-configured libdbus-glib-1-2:amd64 0.100-1ubuntu0.1
2013-03-01 14:15:14 status installed libdbus-glib-1-2:amd64 0.100-1ubuntu0.1
2013-03-01 14:15:14 configure sudo:amd64 1.8.5p2-1ubuntu1.1 <none>
2013-03-01 14:15:14 status unpacked sudo:amd64 1.8.5p2-1ubuntu1.1
2013-03-01 14:15:14 status unpacked sudo:amd64 1.8.5p2-1ubuntu1.1
2013-03-01 14:15:14 status unpacked sudo:amd64 1.8.5p2-1ubuntu1.1
2013-03-01 14:15:14 status unpacked sudo:amd64 1.8.5p2-1ubuntu1.1
2013-03-01 14:15:14 status unpacked sudo:amd64 1.8.5p2-1ubuntu1.1
2013-03-01 14:15:14 status half-configured sudo:amd64 1.8.5p2-1ubuntu1.1
2013-03-01 14:15:14 status installed sudo:amd64 1.8.5p2-1ubuntu1.1
2013-03-01 14:15:14 configure openssl:amd64 1.0.1c-3ubuntu2.2 <none>
2013-03-01 14:15:14 status unpacked openssl:amd64 1.0.1c-3ubuntu2.2
2013-03-01 14:15:14 status unpacked openssl:amd64 1.0.1c-3ubuntu2.2
2013-03-01 14:15:14 status half-configured openssl:amd64 1.0.1c-3ubuntu2.2
2013-03-01 14:15:14 status installed openssl:amd64 1.0.1c-3ubuntu2.2
2013-03-01 14:15:15 configure boot-sav:all 3.197~ppa34~quantal <none>
2013-03-01 14:15:15 status unpacked boot-sav:all 3.197~ppa34~quantal
2013-03-01 14:15:15 status half-configured boot-sav:all 3.197~ppa34~quantal
2013-03-01 14:15:15 status installed boot-sav:all 3.197~ppa34~quantal
2013-03-01 14:15:15 configure boot-repair:all 3.197~ppa34~quantal <none>
2013-03-01 14:15:15 status unpacked boot-repair:all 3.197~ppa34~quantal
2013-03-01 14:15:15 status unpacked boot-repair:all 3.197~ppa34~quantal
2013-03-01 14:15:15 status half-configured boot-repair:all 3.197~ppa34~quantal
2013-03-01 14:15:15 status installed boot-repair:all 3.197~ppa34~quantal
2013-03-01 14:15:15 configure boot-sav-extra:all 3.197~ppa34~quantal <none>
2013-03-01 14:15:15 status unpacked boot-sav-extra:all 3.197~ppa34~quantal
2013-03-01 14:15:15 status half-configured boot-sav-extra:all 3.197~ppa34~quantal
2013-03-01 14:15:15 status installed boot-sav-extra:all 3.197~ppa34~quantal
2013-03-01 14:15:15 configure firefox:amd64 19.0+build1-0ubuntu0.12.10.2 <none>
2013-03-01 14:15:15 status unpacked firefox:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:15 status unpacked firefox:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:15 status unpacked firefox:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:15 status unpacked firefox:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:15 status unpacked firefox:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:15 status half-configured firefox:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:16 status installed firefox:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:16 configure firefox-globalmenu:amd64 19.0+build1-0ubuntu0.12.10.2 <none>
2013-03-01 14:15:16 status unpacked firefox-globalmenu:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:16 status half-configured firefox-globalmenu:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:16 status installed firefox-globalmenu:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:16 configure firefox-gnome-support:amd64 19.0+build1-0ubuntu0.12.10.2 <none>
2013-03-01 14:15:16 status unpacked firefox-gnome-support:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:16 status half-configured firefox-gnome-support:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:16 status installed firefox-gnome-support:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:16 configure firefox-locale-en:amd64 19.0+build1-0ubuntu0.12.10.2 <none>
2013-03-01 14:15:16 status unpacked firefox-locale-en:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:16 status half-configured firefox-locale-en:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:16 status installed firefox-locale-en:amd64 19.0+build1-0ubuntu0.12.10.2
2013-03-01 14:15:16 trigproc libc-bin:amd64 2.15-0ubuntu20 <none>
2013-03-01 14:15:16 status half-configured libc-bin:amd64 2.15-0ubuntu20
2013-03-01 14:15:17 status installed libc-bin:amd64 2.15-0ubuntu20
2013-03-02 00:13:34 startup archives unpack
2013-03-02 00:13:36 install bcmwl-kernel-source:amd64 <none> 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:13:36 status half-installed bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:13:37 status unpacked bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:13:37 status unpacked bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:13:38 startup packages configure
2013-03-02 00:13:38 configure bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-02 00:13:38 status unpacked bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:13:38 status half-configured bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:14:11 status installed bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:14:11 status triggers-pending initramfs-tools:all 0.103ubuntu0.2
2013-03-02 00:14:11 trigproc initramfs-tools:all 0.103ubuntu0.2 <none>
2013-03-02 00:14:11 status half-configured initramfs-tools:all 0.103ubuntu0.2
2013-03-02 00:14:32 status installed initramfs-tools:all 0.103ubuntu0.2

Ok the above is what i have after issuing the comman you listed.

Thank you.

---

### Post by greythorne on 2013-03-02
Ok this is weird. Before i shutdown I tried disconnecting the wireless connection, guess what, the laptop was able to shutdown. If i shutdown without disconnecting the wireless connection the laptop will not shutdown.

---

### Post by matt_symes on 2013-03-02
Hi

> **matt_symes said:**
> I suspect that something in your wireless subsystem is causing your system to hang and i want to see if you had a recent update for it.

> 
2013-03-02 00:13:36 install bcmwl-kernel-source:amd64 <none> 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:13:36 status half-installed bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:13:37 status unpacked bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:13:37 status unpacked bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:13:38 startup packages configure
2013-03-02 00:13:38 configure bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3 <none>
2013-03-02 00:13:38 status unpacked bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:13:38 status half-configured bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3
2013-03-02 00:14:11 status installed bcmwl-kernel-source:amd64 5.100.82.112+bdcom-0ubuntu3

> **greythorne said:**
> Ok this is weird. Before i shutdown I tried disconnecting the wireless connection, guess what, the laptop was able to shutdown. If i shutdown without disconnecting the wireless connection the laptop will not shutdown.

That does not surprise me at all.

You had an update to the wireless subsystem and now it's hanging when you shutdown.

Disconnecting from the network allows clean shudown.

You have a couple of options. You can manually disconnect from the network before shutting down as you have done....

....or you can unload the wireless module automatically before shutting down using a script. We can also look at why it's not disconnectiing you from the network cleanly at shutdown.

As you have a workaround i will not post how to do the script, or offer any other advice, as i have another question.

Does it hang if you hibernate or suspend ?

Kind regards

---

