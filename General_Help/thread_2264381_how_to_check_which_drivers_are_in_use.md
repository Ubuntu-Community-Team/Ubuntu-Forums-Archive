---
title: "how to check which drivers are in use"
date: 2015-02-07
forum: General Help
---

### Post by elliotn on 2015-02-07
I currently installed intel drivers using the intel graphic driver installer. How to check if the installed drivers are the one in use.

thanks

---

### Post by ajgreeny on 2015-02-07
Command ```
lspci -nnk | grep -iA2 net
``` will tell all.

---

### Post by elliotn on 2015-02-07
> elliotn@elliotn-Aspire-4315:~$ lspci -nnk | grep -iA2 net

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 15)
	Subsystem: Acer Incorporated [ALI] Device [1025:0124]
	Kernel driver in use: sky2
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Quanta Microsystems, Inc Device [1a32:0105]
	Kernel driver in use: ath5k
elliotn@elliotn-Aspire-4315:~$ 
elliotn@elliotn-Aspire-4315:~$


this is what I get...but there is no information on Intel.

---

### Post by efflandt on 2015-02-07
Apparently ajgreeny must have been thinking of network instead of graphics drivers. Try:```
lspci -nnk | grep -iA2 VGA
```Although, if you have hybrid graphics (like Intel and Nvidia) you might also want to try **3D** in place of **VGA** to see what that shows.

Otherwise look through /var/log/Xorg.0.log and see if that shows info about a specific driver version.

---

### Post by ajgreeny on 2015-02-07
Yes, sorry about that!

I obviously had a big, useless brain-fart.

For even more info than the lspci command try:-
 **sudo lshw -c display**

---

