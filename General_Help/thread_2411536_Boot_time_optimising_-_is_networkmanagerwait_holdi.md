---
title: "Boot time optimising - is networkmanagerwait holding me up?"
date: 2019-01-31
forum: General Help
---

### Post by steve234 on 2019-01-31
Hi there,

Like with all penguin-people I Iike to tinker - and am running Lubuntu 18.04 LTS + i3wm (gaps fork) for "snappines"... My boot time seems long though at 12s (according to systemd), half of which seems to be NetworkManager-wait-online.service. 

Obviously my computer does not boot in 12s, as for some of this time it is doing POST etc... but if I could shave off 6s 

I've had a read of various threads here and on stackexchange, but what I don't understand is:

1) at what point in my systemd log is the GUI loaded - e.g. the login prompt?
2) is the networkmanager wait before or after the login prompt?

System is a Dell XPS M1530:

[INDENT]- Intel 9300 Dual Core Processor
- Nvidia Geoforce 8400M GS
- 8GB ram[/INDENT]

Systemd outputs are as follows:

```


$ systemd-analyze time
Startup finished in 3.379s (kernel) + 9.169s (userspace) = 12.549s
graphical.target reached after 8.987s in userspace

$ systemd-analyze blame
          6.151s NetworkManager-wait-online.service
          2.322s dev-sda1.device
          1.265s networkd-dispatcher.service
          1.179s udisks2.service
          1.050s avahi-daemon.service
           926ms accounts-daemon.service
           918ms grub-common.service
           898ms apport.service
           827ms gpu-manager.service
           803ms swapfile.swap
           802ms pppd-dns.service
           797ms systemd-journal-flush.service
           632ms lightdm.service
           628ms plymouth-quit-wait.service
           488ms NetworkManager.service
           419ms upower.service
           361ms ModemManager.service

... etc

```

---

### Post by Autodave on 2019-01-31
Your boot time is quite short!  I doubt that you are going to get it any faster than that.  Why do you think that is too long?

---

### Post by steve234 on 2019-01-31
That's good to know - like I say, I'm a tinkerer, thought I could save 6 seconds. 

My other motivation for saving time is that I don't have hibernate working ([https://ubuntuforums.org/showthread.php?t=2411539&p=13834571#post13834571](https://ubuntuforums.org/showthread.php?t=2411539&p=13834571#post13834571)) so I'm rebooting a lot more these days.

---

### Post by HermanAB on 2019-01-31
Use a static IP address and route then you don’t need to wait for NM to do its thing.

---

### Post by steve234 on 2019-01-31
Actually a static IP seems to increase boot time by 0.5s:

```
 

$systemd-analyze time Startup finished in 2.950s (kernel) + 10.166s (userspace) = 13.116s
graphical.target reached after 9.974s in userspace

$ systemd-analyze blame
          6.507s NetworkManager-wait-online.service
          1.395s dev-sda1.device
          1.281s systemd-logind.service
          1.056s udisks2.service
          1.034s systemd-journal-flush.service
           855ms NetworkManager.service
           728ms ModemManager.service
           676ms swapfile.swap
           550ms avahi-daemon.service
           516ms accounts-daemon.service
           432ms lightdm.service
           426ms plymouth-quit-wait.service
           401ms upower.service


```

---

