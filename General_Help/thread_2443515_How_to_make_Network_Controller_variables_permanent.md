---
title: "How to make Network Controller variables permanent in the Kernel"
date: 2020-05-16
forum: General Help
---

### Post by GhX6GZMB on 2020-05-16
My laptop (HP/Compaq 6910p) has an Intel 82566 NIC, which gives me problems (a sister of the 82579).

In certain situations, eg, hibernate, I get the error message "Detected Hardware Unit Hang" repeatedly.

A solution seems to be turning off gro, gso and tso using:


sudo ethtool -K enp0s25 gro off gso off tso off   (enp0s25 is the ID of my NIC).


I could solve this by running a script at start up, but would much prefer fixing the parameters in a settings file for future permanence.


I welcome any suggestion, I'm certain that there are settings controlling the NIC, but have no idea where.

My system (20.04) does not contain proprietary drivers, but relies on the kernel and is freshly updated since yesterday.


Thank You.

---

