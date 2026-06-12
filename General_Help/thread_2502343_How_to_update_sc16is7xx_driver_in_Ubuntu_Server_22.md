---
title: "How to update sc16is7xx driver in Ubuntu Server 22.04 LTS with 5.15.0-1065-raspi"
date: 2024-11-10
forum: General Help
---

### Post by tc2020 on 2024-11-10
I use RPi4 with SC16IS752 dual UART spi chip. The device runs on Ubuntu Server 22.04 LTS, kernel 5.15.0-1065-raspi currently. 

Prior to about 5.15.0-1053-raspi kernel version, I can get data from both UARTs. However, with new versions thereafter, I can only get data from UART 0.  
It seems the newer sc16is7xx driver has changes in data handling that affects my device operation. In either case, I can see in the dev directory both ttySC0 and ttySC1.

How do I fix this issue properly, so that it can handle future kernel updates more readily?. 

Any help would be greatly appreciated. Thank you.

---

### Post by julian552 on 2024-11-21
Before going any further, first examine the system logs for any errors or messages regarding UARTs after the system boots.

[RIGHT][URL="https://1921681001.id/"][COLOR=#a9a9a9][SIZE=1]
192.168.100.1[/SIZE][/COLOR][/URL] [[COLOR=#a9a9a9][SIZE=1]192.168.1.1[/SIZE][/COLOR]]("https://19216811.cam/")[/RIGHT]

---

