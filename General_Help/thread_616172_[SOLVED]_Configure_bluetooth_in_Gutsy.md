---
title: "[SOLVED] Configure bluetooth in Gutsy?"
date: 2007-11-17
forum: General Help
---

### Post by vishzilla on 2007-11-17
I am trying to configure Bluetooth in Gutsy for my Bluetooth-enabled phone. I am able to pair the device, but while trying to send a file from my phone, my computer is not detected. I edited the /etc/bluetooth/hcid.conf file and changed the passkey. Also edited the /etc/rc.local file and entered this line ```
hciconfig hci0 inqmode 0
```. Yet, unable to do so

Kindly help!

EDIT: never mind, solved it!!!!

---

