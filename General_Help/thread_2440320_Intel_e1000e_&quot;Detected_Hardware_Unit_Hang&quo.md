---
title: "Intel e1000e &quot;Detected Hardware Unit Hang&quot;- solution found, need implementation help"
date: 2020-04-08
forum: General Help
---

### Post by GhX6GZMB on 2020-04-08
The Intel e1000e NIC (1Gb Ethernet) has known problems.
I've found a solution, but am unhappy with it.

Installing ethtool and running:

    **sudo ethtool -K eth0 tso off**

solves the problem temporarily. TSO is a low-level (HW) parameter for the e1000e NIC.

I could of course write a script to run when booting, including the above command.

BUT: I'd much rather place this NIC parameter in one of the existing configuration files.

Does anyone have an idea which configuration file controls the NIC and how the parameter should be set?

Thank You.

---

### Post by norobro on 2020-04-09
Looks like that can be handled by systemd. 

See man systemd.link. Specifically: [https://www.freedesktop.org/software/systemd/man/systemd.link.html#TCPSegmentationOffload=](https://www.freedesktop.org/software/systemd/man/systemd.link.html#TCPSegmentationOffload=)

I'll leave it to you to muddle through the config file syntax :smile:

---

