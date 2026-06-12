---
title: "boot takes time in rc-local"
date: 2018-02-10
forum: General Help
---

### Post by axe87 on 2018-02-10
Hi,

I've been investigating how to decrease the boot time of desktop running Ubuntu. I've tried a number of things:

[LIST=1]
[*]Disabled plymouth[https://ask.fedoraproject.org/en/question/33515/fedora19-improving-boot-timedisabling-useless-services/]("https://ask.fedoraproject.org/en/question/33515/fedora19-improving-boot-timedisabling-useless-services/"), 
[*]Deferred apt-daily [https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service]("https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service") 
[*]Removed network-online.target dependency from rc-local [https://askubuntu.com/questions/753909/help-understanding-and-debugging-slow-boot-with-systemd-network-online-target]("https://askubuntu.com/questions/753909/help-understanding-and-debugging-slow-boot-with-systemd-network-online-target")
[/LIST]

This has reduced boot time by about ten seconds. However systemd-analyze still tells me that rc-local is taking 12+ seconds.

```
Startup finished in 3.623s (kernel) + 14.415s (userspace) = 18.038s
         12.435s rc-local.service
          7.404s NetworkManager-wait-online.service
          3.588s fwupd.service
          1.811s accounts-daemon.service
          1.767s udisks2.service
          1.749s ModemManager.service
          1.749s snapd.service
          1.704s NetworkManager.service
          1.530s grub-common.service
          1.400s bluetooth.service
          1.257s avahi-daemon.service
           907ms apt-daily.service
           890ms dev-sdb5.device
           872ms keyboard-setup.service
           849ms systemd-logind.service
           837ms colord.service
           433ms polkit.service
           412ms postfix@-.service
           276ms systemd-modules-load.service

```

```
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @14.409s
&#9492;&#9472;gdm.service @14.389s +19ms
  &#9492;&#9472;rc-local.service @1.952s +12.435s
    &#9492;&#9472;basic.target @1.853s
      &#9492;&#9472;sockets.target @1.853s
        &#9492;&#9472;snapd.socket @1.849s +3ms
          &#9492;&#9472;sysinit.target @1.845s
            &#9492;&#9472;systemd-timesyncd.service @1.663s +182ms
              &#9492;&#9472;systemd-tmpfiles-setup.service @1.645s +13ms
                &#9492;&#9472;local-fs.target @1.644s
                  &#9492;&#9472;home-adrian-gdrive.mount @1.411s +232ms
                    &#9492;&#9472;home.mount @1.355s +24ms
                      &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-9811366d\x2d694a\x2d400b\x2d
                        &#9492;&#9472;dev-disk-by\x2duuid-9811366d\x2d694a\x2d400b\x2db277\x2dc56
```

When I look at what rc-local is doing, I can't see why it would take that much time. It just runs vtrim -v on /, /opt and /home

Presumably it shoul'nt be taking this long or am I misreading something.

Ubuntu 17.10
Intel® Core™ i5-4250U CPU @ 1.30GHz × 4
8 GB
64-bit

---

