---
title: "not able to turn on wifi ubuntu 13.04"
date: 2013-07-05
forum: General Help
---

### Post by AbhimanyuAryan on 2013-07-05
when i go to settings...network and try to slide to toggle button to on....is slides and again comes back to its off position........it doesn't turn on but in ubuntu 12.10 my wifi worked fine but hell not working now.....plz help):P

---

### Post by kc1di on 2013-07-05
Hi,
Let's start with what wireless card your using.  if you don't know please type the following command in a terminal and post the output here. 

```
lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
```

Also type this command and list the output:
```
rfkill list all
```

---

### Post by AbhimanyuAryan on 2013-07-05
> **kc1di said:**
> Hi,
Let's start with what wireless card your using.  if you don't know please type the following command in a terminal and post the output here. 

```
lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
```

Also type this command and list the output:
```
rfkill list all
```

for 1st command:
cooldudeabhi@cooldudeabhi-Studio-1450:~$ lspci -nn | grep -e '\[0200\]' -e '\[0280\]'
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
06:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
cooldudeabhi@cooldudeabhi-Studio-1450:~$ 

for 2nd command:
cooldudeabhi@cooldudeabhi-Studio-1450:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
cooldudeabhi@cooldudeabhi-Studio-1450:~$ 

hope this helps

---

### Post by kc1di on 2013-07-06
Ok the RF kill command says that the WIFI card is turned off.  there should be a key on your machine that will turn it on.

you can try this command in a terminal and see if it will do it:

```
rfkill unblock all
```

other than that if you have a user's manual see what combination of keys turns wireless on and off.

---

### Post by AbhimanyuAryan on 2013-07-06
it worked thanks:p

---

### Post by kc1di on 2013-07-06
Glad it worked for you :)
enjoy.

---

