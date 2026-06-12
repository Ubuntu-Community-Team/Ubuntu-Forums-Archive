---
title: "slow boot apt-daily.service"
date: 2018-07-20
forum: General Help
---

### Post by TaiChiRabbit on 2018-07-20
I'm getting a slow boot time problem with apt-daily service apparently holding up the boot.

```
systemd-analyze blame
```

 > 
     42.842s apt-daily.service
     27.222s apt-daily-upgrade.service
     17.594s systemd-journal-flush.service
     17.570s dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
     17.518s keyboard-setup.service
     17.178s systemd-udevd.service
      6.791s plymouth-quit-wait.service
      6.280s NetworkManager-wait-online.service
      5.056s bolt.service

 I've altered the apt-daily timer config to the below using
 ```
sudo systemctl edit apt-daily.timer
```

> #apt-daily timer configuration override
[Timer]
OnBootSec=15min
OnUnitActiveSec=1d
AccuracySec=1h
RandomizedDelaySec=30min

 but still get the above times. Can anyone explain why the apt-daily service is still running on boot when I'm specifying it to run after 15mins? Thanks

---

### Post by TheFu on 2018-07-21
You don't need it, though it does some things that many people like.  The description says: 
```
Description=Daily apt download activities
```

You can remove the package, but you'll want to manually update the package manager, as needed, somehow.  There are other packages which need to be removed and some systemd settings which need to be modified to prevent attempts.

I patch weekly and manually run the update just before doing that.  If there is a high risk machine I'm managing and a high risk patch is release, I'll manually install it as needed,only on the systems with the risk.  That's happened about 3 times in 15 yrs.

You might need to manually autoclean and autoremove packages to prevent full filesystems too.  Never let a filesystem get get really full (for certain values of "full").  Mainly, only let /boot have less than 200MB of free storage and don't let / have less than 1G free.  Those are rules of thumb.

---

### Post by kazakore on 2018-07-21
That was the first item I saw reported with what turned out to be the -24 kernel bug causing slow boot times. My upgrade today pulled down a new kernel so try issuing an apt dist-upgrade and see if you still have the same problem.

---

### Post by TaiChiRabbit on 2018-07-22
Thank you...I'm running Linux desktop 4.15.0-29 on Ubuntu 18.04.  This morning slightly faster boot, but still confused why apt-daily service running on boot when the config file is set for 15minutes....

> 
         18.086s dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
         17.941s keyboard-setup.service
         17.766s apt-daily.service
         17.731s systemd-journal-flush.service
         17.448s lvm2-monitor.service
         17.266s systemd-udevd.service
          6.392s NetworkManager-wait-online.service
          5.149s plymouth-quit-wait.service
          5.047s bolt.service
          1.515s apt-daily-upgrade.service



---

