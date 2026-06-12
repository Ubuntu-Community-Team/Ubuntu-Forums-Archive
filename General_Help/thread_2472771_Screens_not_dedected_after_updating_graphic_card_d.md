---
title: "Screens not dedected after updating graphic card driver"
date: 2022-03-12
forum: General Help
---

### Post by lo-sy on 2022-03-12
Ubunto version: 20.04.4
Graphic card: geforce gtx 1060 6gb
Dual boot with windows 10.

[COLOR=#333333][FONT=&amp]I installed linux on my PC (dual boot). The nvidia driver wasn’t properly installed so I updated it from the terminal. [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]When I restarted the PC, both screens stay in save mode until the linux boots. So I don’t see the BIOS options nor the options to boot windows as both screens are off the whole time.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]When linux boots, it also get stuck on the logo lol.
[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]When Linux is stuck at the logo windo, I managed to access the terminal by pressing alt+ctr+f7 where I log in to my account via terminal.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]I modified the gurb file to boot in Nomodoset mode but now I only get black screens all the time. Both screen are in save mode.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]What is funny, if I blindly press alt+ctr+f7 to access the terminal and write ‘Reboot’, the PC restart but nothing on the screens. 

I am very surpried how could a driver update cases the such sever impact on the PC booting. As far as I am concered, the driver update is installed on the operating system, so why it is preventing the graphic card to work from the start up? 

please advise

Thanks[/FONT][/COLOR]

---

### Post by texpat on 2022-03-12
I had a very similar issue with my nvidia gtx 1050 and installing the version 510 drivers. Both screens dead, basically. What I did was to physically remove the graphics card and use the on-board graphics to get a gui and roll back driver installation. Put the card back in and installed the nvidia-driver-470 drivers and things started working again. Still glitchy when I turn off the monitors for a while (have to reconfigure monitor layout).

---

