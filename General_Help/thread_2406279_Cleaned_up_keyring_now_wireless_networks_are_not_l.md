---
title: "Cleaned up keyring now wireless networks are not listed"
date: 2018-11-18
forum: General Help
---

### Post by Heeter on 2018-11-18
Hi all,

I was in the keyring and I was removing some what I thought was unneeded logins

Now the wireless is disconnected and I can't see any wireless list showing up.

I reinstalled the broadcom driver, to no effect.

Ran the rfkill command:
```

adminpc@adminpc:~$ lspci -knn | grep Net -A2; rfkill list
02:00.0 Network controller [0280]: Broadcom Limited BCM43228 802.11a/b/g/n [14e4:4359]
	Subsystem: Dell BCM43228 802.11a/b/g/n [1028:0014]
	Kernel driver in use: wl
--
0c:00.0 Ethernet controller [0200]: Broadcom Limited NetXtreme BCM5761 Gigabit Ethernet PCIe [14e4:1681] (rev 10)
	Subsystem: Dell NetXtreme BCM5761 Gigabit Ethernet PCIe [1028:053c]
	Kernel driver in use: tg3
	Kernel modules: tg3
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
adminpc@adminpc:~$ 

```

Any help would be greatly appreciated

---

