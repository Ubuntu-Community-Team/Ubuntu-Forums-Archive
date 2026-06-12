---
title: "Ksystemlog : please install nss-myhostname !"
date: 2016-02-29
forum: General Help
---

### Post by valereguerin on 2016-02-29
```
freeman@freeman-Sniper:~$ sudo apt-get install nss-myhostname
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet nss-myhostname
freeman@freeman-Sniper:~$
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet nss-myhostname
freeman@freeman-Sniper:~$
```

```
freeman@freeman-Sniper:~$ inxi -b
System:    Host: freeman-Sniper Kernel: 3.13.0-80-generic x86_64 (64 bit) Desktop: Gnome 3.10.4 Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award version: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 CPU 930 (-HT-MCP-) clocked at 2860.105 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280] 
           X.Org: 1.15.1 drivers: ati,fglrx (unloaded: fbdev,vesa,radeon) Resolution: 1920x1080@60.0hz 
           GLX Renderer: AMD Radeon HD 7900 Series GLX Version: 4.5.13399 - CPC 15.20.1013
Network:   Card-1: D-Link System DGE-528T Gigabit Ethernet Adapter driver: r8169 
           Card-2: Realtek RTL8187 Wireless Adapter driver: rtl8187 
Drives:    HDD Total Size: 5815.3GB (32.4% used)
Info:      Processes: 302 Uptime: 14:42 Memory: 5237.2/7982.7MB Client: Shell (bash) inxi: 1.9.17
```

```
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet libnss_myhostname.so.2
E: Impossible de trouver de paquet correspondant à l'expression rationnelle « libnss_myhostname.so.2 »
```

---

### Post by slickymaster on 2016-02-29
See this: [What is nss-myhostname? And why is it not installable?]("http://askubuntu.com/questions/453072/what-is-nss-myhostname-and-why-is-it-not-installable")

---

### Post by valereguerin on 2016-02-29
thanks for help !

---

