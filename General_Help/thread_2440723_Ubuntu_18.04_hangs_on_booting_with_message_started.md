---
title: "Ubuntu 18.04 hangs on booting with message started user manager for uid"
date: 2020-04-14
forum: General Help
---

### Post by jape258 on 2020-04-14
the message is just.
  ```
[ok] Started user manager for uid 121
[COStopping user manager for uid 121
```
I have tried to uncomment WaylandEnable=false in /etc/gdm3/custom.conf I have also tried to use lightdm

 **[FONT=&quot]Dell OptiPlex 990[/FONT]**
  [COLOR=#4472C4][FONT=&quot]Processor[/FONT][/COLOR]
  [FONT=Symbol]·         [/FONT][FONT=&quot]Intel® Core&#8482; i7 2600 / 3.40GHz, 8M, VT-x, VT-d, TXT (vPro&#8482;), 95W[/FONT]
  [COLOR=#4472C4][FONT=&quot]Motherboard[/FONT][/COLOR]
  [FONT=Symbol]·         [/FONT][FONT=&quot]dell e93839 ka0121[/FONT]
  [COLOR=#4472C4][FONT=&quot]Memory[/FONT][/COLOR]
  [FONT=Symbol]·         [/FONT][FONT=&quot]8GB of ram[/FONT]
  [COLOR=#4472C4][FONT=&quot]Drive[/FONT][/COLOR]
  [FONT=Symbol]·         [/FONT][FONT=&quot]1TB of HDD[/FONT]
  [COLOR=#4472C4][FONT=&quot]Graphics[/FONT][/COLOR]
  [FONT=Symbol]·         [/FONT][FONT=&quot]Intel HD Graphics[/FONT]
  [COLOR=#4472C4][FONT=&quot]Communications[/FONT][/COLOR]
  [COLOR=#70AD47][FONT=&quot]            Network Adapter[/FONT][/COLOR]
  [FONT=Symbol]·         [/FONT][FONT=&quot]Intel® 82579LM Gigabit1Ethernet LAN 10/100/1000[/FONT]

---

### Post by Claus7 on 2020-04-14
Hello,

uid I suppose is the user id message. Have you tried creating a new user and see if you are getting the same problem?

Regards!

---

