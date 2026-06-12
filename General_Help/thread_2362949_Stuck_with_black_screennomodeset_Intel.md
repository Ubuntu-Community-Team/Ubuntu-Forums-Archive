---
title: "Stuck with black screen/nomodeset Intel"
date: 2017-06-04
forum: General Help
---

### Post by rossbishop on 2017-06-04
[COLOR=#444444][FONT=Helvetica]I've been trying with moderate success to do GPU passthrough with Ubuntu 16.04. I had the passthrough into a Windows VM working, able to play games etc.[/FONT][/COLOR]
[COLOR=#444444][FONT=Helvetica]However, the Intel graphics have been an absolute pain in my ****. So much so I decided to start from scratch and get them working properly before moving on.[/FONT][/COLOR]
[COLOR=#444444][FONT=Helvetica]I'm using with a 7700K (630 iGPU) set to primary graphics device in the BIOS and a GTX 1070 in my PCI-E 16X on my ITX motherboard.[/FONT][/COLOR]
[COLOR=#444444][FONT=Helvetica]From the beginning, booting Ubuntu LiveCD without a black/purple frozen requires me to edit the "Ubuntu" entry in the menu by hitting "e" and adding "nomodeset" to the parameters. Hit F10, I can boot to a desktop with full resolution.[/FONT][/COLOR]
[COLOR=#444444][FONT=Helvetica]If I then make this change permanent by making the change in /etc/default/grub, after a reboot I get a lovely 1024x768 desktop with no increased resolution options.[/FONT][/COLOR]
[COLOR=#444444][FONT=Helvetica]Tried the Intel graphics update utility and nomodeset removed from grub, and it goes back to square one.[/FONT][/COLOR]
[COLOR=#444444][FONT=Helvetica]I really don't know what to do to solve this issue. It's frustrating since I've had everything else working before but haven't managed to get the Intel drivers working properly.[/FONT][/COLOR]
[COLOR=#444444][FONT=Helvetica]Any suggestions would be much appreciated. Any debugging information you want I can go and find.[/FONT][/COLOR]

---

