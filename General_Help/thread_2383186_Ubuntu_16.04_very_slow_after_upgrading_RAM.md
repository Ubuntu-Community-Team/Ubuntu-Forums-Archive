---
title: "Ubuntu 16.04 very slow after upgrading RAM"
date: 2018-01-22
forum: General Help
---

### Post by pokemon4e on 2018-01-22
I have an Hp probook 450 g2:
[COLOR=#000000][FONT=inherit]Processor: Intel Core i5-5200 CPU @ 2.20GHz x 4
Graphics: Intel HD Graphics 5500 (Broadwell GT2)
SSD: 128GB [/FONT][/COLOR][COLOR=#000000][FONT=&quot]Transcend[/FONT][/COLOR][COLOR=#000000][FONT=inherit]
Supports up to 16GB of RAM

It came with one RAM stick of 4GB (Samsung 4096 MB RAM @ 1600 MHz). Recently I bought an additional one - 8GB (Hynix/Hyundai 8192 MB RAM @ 1600 MHz) and installed both (12 GB in total). 

I  run dual boot: Ubuntu 16.04 and Windows 10 (both 64 bit). In Windows everything works just fine. However, when running Ubuntu, it is very very slow - few minutes to boot and it takes 1 min to open the terminal or any other program. I tried fresh install of Ubuntu 16.04 and 17.10 and both are again very slow. 

However, if I remove one of the RAM sticks (it does not matter which one) and reboot, it is fast again. I have tried running Ubuntu from the USB ("Try Ubuntu without installing" option) and it works well.

I am fairly new to Ubuntu (and linux), so please let me know what other information should I provide.
Any help is highly appreciated[/FONT][/COLOR][FONT=inherit][FONT=inherit][FONT=inherit][COLOR=#1D2129][FONT=&quot][COLOR=#FFFFFF][FONT=inherit][/FONT][/COLOR]
[/FONT][/COLOR]
[/FONT]
[/FONT]
[/FONT]

---

### Post by mastablasta on 2018-01-22
do you have any swap partition setup?

this is strange. it could be incompatible RAM. linux uses RAM differently than windows so it could just be that the issue in windows hasn't manifested yet.

you might also dig into the user manual and check all bios settings.

---

### Post by pokemon4e on 2018-01-22
I have a swap partition (6 GB). Running **top** shows that it is not used. 

[COLOR=#000000][FONT=&amp]As far as I can tell, the two RAM sticks should be compatible. Both are DDR3L since this is what the laptop model expects. 

I have also checked the two memory sticks in Windows using the application CPU-Z and both sticks have the same frequency. I have also gone through the different BIOS settings and couldn't find any that pertain to RAM. 

What puzzles me most is that when booting from a live USB everything works. Are there any special boot arguments that u Ubuntu uses when booting from USB?[/FONT][/COLOR]

---

### Post by mastablasta on 2018-01-22
yes, the frequency might be the same, but they can still be incompatible. since you say it works well using one stick.

live USB loads the whole OS to RAM when it boots. while normal boot loads only some things.

memtest will test the ram. though i doubt anything is wrong.

---

### Post by cruzer001 on 2018-01-22
Could it be the kernel?  The live DVD uses a different kernel I bet.

---

### Post by pokemon4e on 2018-04-19
Hi there, 

It might be a bit late, but I ended up buying another RAM stick 8GB (Hynix/Hyundai 8192 MB RAM @ 1600 MHz). So I run Ubuntu with 2 same RAM sticks 8GB (Hynix/Hyundai 8192 MB RAM @ 1600 MHz). However, the problem persisted. Eventually, I returned the laptop, as it was still in warranty.

---

