---
title: "Problem after replacement of hard disk"
date: 2020-04-05
forum: General Help
---

### Post by alo12 on 2020-04-05
Hello, i am running the latest version of xubuntu LTS to this system _*3 Intel Xeon CPU E5405 2.00GHz &#8214; RAM 3949 MiB &#8214; Dell Inc. 0RW203 - Dell Inc. Precision WorkStation T5400*__*4 nVidia G84GL [Quadro FX 570] [10de:040e] {nouveau} &#8942; nVidia G84GL [Quadro FX 570] [10de:040e] {nouveau}*_
[U][I]5 eth0: Broadcom NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)

[/I][/U]I have decided  to replace my ten years old hdd with an SSD (SAMSUNG 860 EVO), i used clonezilla for the immigration to the new hard disk. Unfortunately after the immigration to the ssd the system freezes a lot and i am forced to restart it often. Could you help me find out what is going wrong?

Thank you in advance

---

### Post by lvm on 2020-04-05
Nouveau is not reliable, replace it with proprietary nvidia driver. Checking last messages in /var/log/syslog is also a good idea.

---

### Post by TheFu on 2020-04-05
Check the log files for issues.  They are all in /var/log.  Best to grep for errors and warnings across all the log files to get a feeling, then use a file pager (less/more) to find the specific places with issues and check a few lines above and below the issue.

I have a Samsung 860 on my core i5 laptop and it is very solid.  The sector size on mine is 512b, so that shouldn't be any issue for misaligned stuff - some storage will use 4Kb sectors, usually if the disk is over 1TB in size.

An SSD that freezes or goes read-only usually means it is about to fail.  I'd look at the **SMART** data for it ASAP to see if there are any hints.  Sometimes, it is just a bad cable, so that would be an easy fix on a desktop, but less easy to fix on a laptop.

---

### Post by TheFu on 2020-04-05
> **lvm said:**
> Nouveau is not reliable, replace it with proprietary nvidia driver. Checking last messages in /var/log/syslog is also a good idea.

Old Quadro devices don't have proprietary drivers that work with newer Linux kernel versions.  I ended up giving a way a workstation Quadro CAD card because support ended with 14.04.

---

