---
title: "update-notifier/apt-check does not show available updates on 14.04 LTS"
date: 2014-08-23
forum: General Help
---

### Post by stephan9 on 2014-08-23
I noticed that even after apticron sent me a message about available updates on my next login the motd (dynamically created by pam_motd) does show 0 updates.

I tried to figure out what's happening. The script [FONT=courier new]/etc/update-motd.d/90-updates-available[/FONT] is calling apt-check. I tried to verify by manually calling and got this: 

```
sudo /usr/lib/update-notifier/apt-check --human-readable
0 packages can be updated.
0 updates are security updates.

```

aptitude is well aware of available updates:
```
sudo aptitude upgrade
The following packages will be upgraded:
  python3-distupgrade ubuntu-release-upgrader-core
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So to me it looks like a bug in apt-check as it did not report these two available updates.

Is anyone else experiencing this? My python fluency is not good enough to dig further into apt-check. 
Is this a bug which should be reported somewhere? I'm quite new to ubuntu and have no idea what the proper bug reporting process is. So pointers to some howto would be appreciated.

Thanks for advise.

---

