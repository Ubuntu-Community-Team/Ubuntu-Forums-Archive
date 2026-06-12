---
title: "Help with network devices on laptop"
date: 2020-10-30
forum: General Help
---

### Post by sniper8752 on 2020-10-30
I have a wireless card and a ethernet jack (via usb-c) that I am using.  How do I know which one is the default/preferred, and which one it is using?  I assume it is not using both for "faster speeds".  How do I tell it to use one over another?

---

### Post by SeijiSensei on 2020-10-30
If you don't turn on the wireless, it will use the Ethernet adapter. If you don't connect anything to the Ethernet port, it will default to wireless.

And, you're right that connecting both will not by itself improve performance. You can consider using "[bonding]("https://help.ubuntu.com/community/UbuntuBonding")." In fact, having them both connected to the same upstream router can cause routing problems.

---

