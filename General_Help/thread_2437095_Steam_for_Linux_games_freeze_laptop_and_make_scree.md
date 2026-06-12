---
title: "Steam for Linux games freeze laptop and make screen flicker"
date: 2020-02-18
forum: General Help
---

### Post by Hatgor on 2020-02-18
[COLOR=#22231F][FONT=&quot]Hello everybody![/FONT][/COLOR][COLOR=#22231F][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#22231F][FONT=&quot]I've faced a very strange issue with a new laptop - Razer Blade Stealth / Intel Core i7-1065g7 / No discrete GPU.[/FONT][/COLOR]
[COLOR=#22231F][FONT=&quot]I've installed Kubuntu 19.10 (Kernel 5.3) and Steam for Linux, but each time I tried to launch any game via Steam my laptop freezes and I have to reboot it.[/FONT][/COLOR]
[COLOR=#22231F][FONT=&quot]After reboot the screen starts flickering and I had to reboot the laptop 3-4 times - each time after reboot the flickering decreases.[/FONT][/COLOR]
[COLOR=#22231F][FONT=&quot]The most weird detail is that the screen keeps flickering even in BIOS![/FONT][/COLOR]
[COLOR=#22231F][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#22231F][FONT=&quot]Please advise what is the reason of this issue and how to solve it. [/FONT][/COLOR]

---

### Post by mastablasta on 2020-02-18
> **Hatgor said:**
> 
[COLOR=#22231F][FONT=&amp]The most weird detail is that the screen keeps flickering even in BIOS![/FONT][/COLOR]


this indicates a hardware issue. 

can you maybe upgrade BIOS?


as for OS you could try new LTS 20.04 (still in beta), as it has newer kernel.

---

### Post by Hatgor on 2020-02-18
> **mastablasta said:**
> this indicates a hardware issue. 

can you maybe upgrade BIOS?

as for OS you could try new LTS 20.04 (still in beta), as it has newer kernel.

Not sure about BIOS upgrade is necessary - the laptop is late 2019. LTS 20.04 is a good idea but I'll wait the release date. 

Need to be mentioned - I've tried today to install and launch games from desktop kubuntu store - 0 A.D. for example. 
It runs good, with no freeze or flickering. 

Same issue (freeze + flickering) occurs when I tried to launch Windows games via Wine. 

Will this info help?

---

### Post by _sge on 2020-02-19
The fact that the screen flickers even in BIOS may indicate faulty hardware eg, faulty RAM or faulty GPU. Does the same flickering issue happen in other operating system like Windows?It's definitely worth double checking the BIOS and making sure it's the latest version. Check the BIOS release notes to see if they fixed a flickering issue.Since your laptop is from late 2019, you're probably right that the kernel and drivers in Ubuntu 20.04 will better support your hardware and fix the issue, but first rule out any hardware faults.

---

