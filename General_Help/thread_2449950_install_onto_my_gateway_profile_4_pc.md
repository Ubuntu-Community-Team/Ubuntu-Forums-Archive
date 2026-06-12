---
title: "install onto my gateway profile 4 pc"
date: 2020-09-04
forum: General Help
---

### Post by jboscoe on 2020-09-04
I have an older gateway all in one profile 4 pc. It has 2gb memory and 2.4 ghz cpu. I reinstalled windows xp3 to make sure hardware still worked now i want to install lubuntu onto the second partition in order to dual boot.them.  Live usb worked great and the install to the harddrive worked good it boots to the desktop then it can't access the usb or ethernet on this machine. Is there a way to correct this or am i to give up.  No matter which linux distro i install to this hard drive it will not support the usb or ethernet. The ethernet shows a 127 ip address which is wrong and i am unable to run my wifi adapters from usb due to this issue.  I have used ubuntu on many differnet older pc's but this the first one thats stumped me.  Thanks in advance to the designers of the many distro and thanks.  Take care and God Bless from Joe of upstate new york.

---

### Post by guiverc on 2020-09-04
Some specifics may help.

You mentioned Lubuntu, but no release details, nor what ISO you installed from. The actual ISO details would tell me what release, what software stack (eg. LTS release have two software stacks offered, 18.04 & 18.04.1 media will use the GA or generic kernel & stack, but later media (18.04.2 and above) uses the HWE or hardware-enablement stack, meaning later kernel, video kernel modules etc (~drivers)   *(I used 18.04 as example, as currently there is no difference for Lubuntu 20.04 with both GA & HWE stacks still being the same, we've not got to 20.04.2 release yet)*

I would firstly list hardware of class network (`sudo lshw -C network`) to see if network hardware is recognized. Were the devices (ethernet & USB ports) recognized during the *live* session pre-install (you didn't say which release or which ISO you installed, so I'm assuming you used a *live* installer) or is this an issue now post-install only?

---

### Post by jboscoe on 2020-09-05
sorry i thought i had given that information. The release is 18.04.3 and i installed it from my external usb.  But like i said it didn't matter if the live version worked when i install to hard drive i lose all usb and ethernet support or drivers. Being a new user i am curious how to correct this if possible.  Thanks in advance for the replay and like i said God Bless and be safe.  Sincerely Joe

---

### Post by jboscoe on 2020-09-05
Also i will boot it up and use your command to see if they are reconized. Thanks Joe

---

### Post by jboscoe on 2020-09-05
sorry to be a pest this issue is post install. I used your sudo show command and it showed only the ethernet interface here is that info below but the usb ports aren't recoinized after post install sorry for the typos.  the description shows.  product: 8280IDE pro/100 ve lcm ethernet controller  vendor: intel corp.   physical id:  8  bus info: pci@0000.02....08.0   logical name: enp2s8  version: 81  serial: 00:e0:b8:4c:48:04  size: 10Mbit/s  capacity:100Mbit/s  width 32bits   clock:33mhz  capabilities: pm bus_master cap_list  ethernet physical tp mil 10bt 10bt-fd 100bt  100bt-fd autonegotiation   configuration: autonegotiation=on broadcast=yes  driver=e100  driverversion=3.5.24-k2-NAPI  duplex=half  latency=64  link=no  max:latency=567  mingnt=8  multicast=yes  port=MII  speed=10Mbit/s   resorces:  irg 11  memory:c2005000-c2005fff  ioport:209090(size=64)  but no sign of my usb ports.  Thanks and sorry for the list of issues.  Thanks ever so much sincerely Joe from Upstate NY

---

