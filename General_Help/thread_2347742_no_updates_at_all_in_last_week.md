---
title: "no updates at all in last week?"
date: 2016-12-28
forum: General Help
---

### Post by missmoondog on 2016-12-28
i have 7 different lunbuntu 16.04LTS computers here and none of them have received ANY updates in the last week, or very close to it. am i freaking out or has there actually not been a single update for any program in that amount of time? i can't remember EVER having gone that long without some kind of update. i'm checking using synaptic and software updater.

thank you

---

### Post by howefield on 2016-12-28
Over the holiday season I'd not worry about the lack of updates, it is likely that there are none.

You can keep up to date with what is being updated by subscribing (or browsing) the [Xenial-changes ]("https://lists.ubuntu.com/mailman/listinfo/xenial-changes")mailing list.

You might also check the /var/log/apt/history.log file for any packages that unnattended-upgrades has updated in the background.

---

### Post by vasa1 on 2016-12-28
The last upgrade I had was:```
Start-Date: 2016-12-21  04:36:38
Commandline: apt-get dist-upgrade
Requested-By: vasa1 (1000)
Install: linux-image-4.4.0-57-generic:amd64 (4.4.0-57.78, automatic), linux-image-extra-4.4.0-57-generic:amd64 (4.4.0-57.78, automatic), linux-headers-4.4.0-57-generic:amd64 (4.4.0-57.78, automatic), linux-headers-4.4.0-57:amd64 (4.4.0-57.78, automatic)
Upgrade: linux-headers-generic:amd64 (4.4.0.53.56, 4.4.0.57.60), linux-libc-dev:amd64 (4.4.0-53.74, 4.4.0-57.78), linux-image-generic:amd64 (4.4.0.53.56, 4.4.0.57.60), linux-generic:amd64 (4.4.0.53.56, 4.4.0.57.60)
End-Date: 2016-12-21  04:39:01

```

---

### Post by missmoondog on 2016-12-28
thanks vasa! that was the date of my last update also. i know it's the holidays and such, but hard to believe NOTHING was updated in a week.

---

### Post by bbudescu on 2016-12-30
As I can see, there was some activity, some new package versions were added (e.g. network-manager 1.2.4), but package indices were not updated (e.g. [http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-amd64/Packages.gz/Packages-2](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-amd64/Packages.gz/Packages-2) still references version 1.2.2, although version 1.2.4 is available here [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_1.2.4-0ubuntu0.16.04.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_1.2.4-0ubuntu0.16.04.1_amd64.deb) since 23.12.2016). I'm not familiar with the release process. Is there more testing to be done on those versions? Should the indices be generated automatically?

---

### Post by howefield on 2016-12-30
> **bbudescu said:**
> As I can see, there was some activity, some new package versions were added

Yes, there was some activity eg, lxd was updated but there were no updates for packages on the OPs machine.

> (e.g. network-manager 1.2.4)

not for 16.04 which is what the OP is running, although that version (1.2.4) is available for 16.10.

---

