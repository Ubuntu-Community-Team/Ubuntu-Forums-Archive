---
title: "[Ubuntu 20.04.3 LTS] Wi-Fi doesn't work"
date: 2021-09-29
forum: General Help
---

### Post by kentatetsu on 2021-09-29
Hello guys,
My wifi doesn't work and I don't know how to fix it.
I type this command **DMESG** to see what's happening.

Here is a link to see my terminal with the command :
[https://paste.ubuntu.com/p/XrdZkYY3Nv/](https://paste.ubuntu.com/p/XrdZkYY3Nv/)

Please help me and thank you!

---

### Post by grahammechanical on 2021-09-29
Try going into the UEFI/BIOS setting utility to confirm that the WiFi adapter is not disabled. Try these commands

```
nmcli radio all
iwconfig
```

Paste the results in this thread.

Regards

---

### Post by bijayalaxmi1808 on 2021-09-30
r8169 0000:08:00.0 enp8s0: Link is Up - 1Gbps/Full - flow control rx/tx
Here it appears to be the WiFi interface is up.

rtw_8822be 0000:07:00.0: failed to power on mac
But again, here it reports some issue with the MAC.

This is an integrated WiFi and Bluetooth chipset, so, I assume the Bluetooth MAC is not able to come up. Can you please turn off the Bluetooth and see if the WiFi works well?

---

