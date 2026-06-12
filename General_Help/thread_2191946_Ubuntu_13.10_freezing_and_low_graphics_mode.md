---
title: "Ubuntu 13.10 freezing and low graphics mode"
date: 2013-12-05
forum: General Help
---

### Post by shunkow on 2013-12-05
Hi everybody

[COLOR=#333333][FONT=UbuntuRegular]I have installed Ubuntu 13.10 64-bit on my desktop PC, and it seems it's not working properly. I have freezing while typing, the virtual console is not available, if I try go to it my screen is freezing, also the cursor leaves a trace on the screen.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have tried to install Nvidia graphics drivers (from offsite, and from xorg repositories), but after it my Ubuntu doesn't boot. I see only a white blinking underline character cursor in top left corner of a black screen and nothing more. In that case I have to do a hard reboot, because the screen is frozen and I can't make my system respond in any other way.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I also tried to install Ubuntu 12.04, but the loader gives a message about "low graphics mode" and after that I see only a black screen, and I can do nothing.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]For the moment I have reinstalled Ubuntu 13.10, and I am looking for an answer.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Can someone help me?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Specifications of my PC:
&#10240;CPU: Intel Core i5-4670K (Haswell)
&#10240;Motherboard: GigaByte G1.Sniper B5
&#10240;Graphics card:  Asus GTX760-DC2OC-2GD5 

I already asked my question on Ubuntu Aks but I still did not get answer ((.[/FONT][/COLOR]

---

### Post by ibjsb4 on 2013-12-06
I do not run this graphic card, but I did get some hits here that may help you out.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Asus+GTX760&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Asus+GTX760&sa=Search&cof=FORID:9)

---

### Post by shunkow on 2013-12-06
Thank you, it might be useful for me, I still looking for solution.

---

### Post by expatpeter on 2013-12-07
For me the solution will be, to change the motherboard, because my new Gigabyte motherboard does not work after installing the grafic-drivers. Gigabyte told me, that they do not support Linux.

---

### Post by shunkow on 2013-12-07
It is absolutely inappropriate for me, seems my problem can be solved, it's really sad.(

---

### Post by efflandt on 2013-12-07
A common boot parameter sometimes needed during install, and sometimes afterwards is **nomodeset** to use graphic modules instead of kernel mode setting. My i5 is older, so it has no integrated graphics, but not sure if your cpu or board does, in which case you may also need to do something else to specifically use the nvidia graphics (like I had to do in 13.10 for i7 laptop with both integrated Intel and GTX 765M graphics). But it can't hurt to try nomodeset.

Also what type of connection do you have to your monitor? DVI or HDMI may find its native resolution better than VGA.

---

### Post by shunkow on 2013-12-07
I use DVI but I suppose problem not related to connection type... 
About nomodeset, it is interesting idea, if I cant solve the problem in other way I'll try to use nomodeset.
Thanks.

---

### Post by shunkow on 2013-12-08
I have solved the problem by myself. I have installed ubuntu in UEFI mode, not in BIOS. This solution works fine for me.

---

