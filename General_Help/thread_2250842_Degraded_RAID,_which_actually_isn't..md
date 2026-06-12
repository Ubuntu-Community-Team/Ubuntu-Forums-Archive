---
title: "Degraded RAID, which actually isn't."
date: 2014-10-31
forum: General Help
---

### Post by nunecas123 on 2014-10-31
Here's my issue. I rebuilded my RAID-1 Array a while ago, but after I do a reboot, it always gets degraded, saying that one of my drives aren't attached. I also noticed that if I stop and then start the RAID again, it's not degraded anymore(that is, my device is fully synchronized).
I'm using Ubuntu 12.04 LTS by the way.

Is there a way to fix this, like reassemble the RAID-1 Array at startup? Or is there another way of fixing this?
I just hate to stop and start the RAID every time.

Thank you in advance.

---

### Post by tgalati4 on 2014-10-31
Check your power supply.  Perhaps your disks are not spinning up quickly enough to enumerate themselves.  When you restart the RAID, your disks are warmed up and spinning.  Use a voltmeter and check the 12VDC supply.  If it drops more than 10% (10.8VDC) then your power supply needs attention.  If you don't have a voltmeter, use the BIOS "Health Management" or "System Montitor" to view the voltages.

Also check the SMART parameters for each drive:

```
sudo smartctl -a /dev/sdc
```

Use fdisk to get the drive letters:

```
sudo fdisk -l
```

---

### Post by nunecas123 on 2014-10-31
The voltages are ok. I don't really know what's wrong. The S.M.A.R.T. is also good, both drives pass.
I guess it's more of a software problem.

---

