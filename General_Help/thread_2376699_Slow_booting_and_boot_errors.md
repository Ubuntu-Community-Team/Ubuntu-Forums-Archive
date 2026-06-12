---
title: "Slow booting and boot errors"
date: 2017-11-05
forum: General Help
---

### Post by i2000s2 on 2017-11-05
I posted this question on [AskUbuntu]("https://askubuntu.com/questions/973084/very-slow-boot-and-broken-elements-on-ubuntu-16-04"), but haven't received any answers there. So, I am asking if anyone can have a look on the question there and give me some insight. Thanks!

---

### Post by i2000s2 on 2017-11-05
The ```
[FONT=monospace]systemd-udev-settle.service[/FONT]
```[FONT=monospace] is the main factor which slows the booting down. Since I have been using LVM, I cannot turn it off. Is this a bug from kernel? It was ok earlier.
[/FONT]
> 
[FONT=monospace]$ systemd-analyze blame
1min 29.765s systemd-udev-settle.service 
     9.672s NetworkManager-wait-online.service 
     2.955s plymouth-quit-wait.service 
     2.449s upower.service       738ms lvm2-activation-early.service 
      645ms dev-mapper-ubuntuvg\x2droot.device 
      519ms nmbd.service 
      436ms grub-common.service 
      431ms sysfsutils.service 
      430ms dictd.service 
      430ms apport.service 
      423ms irqbalance.service 
      417ms plymouth-start.service 
      416ms speech-dispatcher.service 
      381ms ondemand.service 
      325ms vboxdrv.service 
      312ms media-I.mount 
      291ms lvm2-activation.service 
      237ms media-F.mount 
      213ms lvm2-monitor.service 
      170ms lvm2-activation-net.service 
      163ms systemd-hwdb-update.service 
      155ms media-H.mount
[/FONT]

---

