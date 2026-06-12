---
title: "adb"
date: 2016-11-20
forum: General Help
---

### Post by thomas_j_marshall2 on 2016-11-20
Tried for a while now to get adb working on ubuntu 16.10.  I've lost recovery on my galaxy s5 after flashing a rom (which failed0 and am stuck with download mode only so need adb to push a rom.  Followed a few threads but can't seem to get it to recognise my phone.  Have set android rules in udev.

---

### Post by kingneutron on 2016-12-01
--Try these as root:

adb start-server
adb devices

--I know that USB debugging usually needs to be enabled and the device needs to be connected as an MTP, other than that you may have more luck on an Android forum...

---

