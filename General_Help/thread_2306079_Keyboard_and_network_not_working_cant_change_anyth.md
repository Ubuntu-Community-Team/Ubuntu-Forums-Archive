---
title: "Keyboard and network not working cant change anything to fix either"
date: 2015-12-12
forum: General Help
---

### Post by John_Kreis on 2015-12-12
I have a Mythubuntu backend server running on an AMD Phenom CPU and Asus MOBO I had laying around. I have had issues with USB in general from the beginning. Both keyboard and mouse have worked intermittently but the keyboard hasn't worked in a while, finally got the mouse working somewhat consistently but the cursor stills occasionally dies and sometime I lose the cursor but I can still click. Sometimes I can move the cursor but not click. I do most of my interaction over VNC or SSH so I never too much in fixing it. 

About 10 days ago I did some system updates and my Ceton PCIe tuner card was no longer recognized. I followed Myth's Wiki ([https://www.mythtv.org/wiki/Ceton_InfiniTV_4](https://www.mythtv.org/wiki/Ceton_InfiniTV_4)) and modified the file. After a reboot my network interface is no longer working. So currently I have no way to interact with the server. I can use the mouse but I dont think I can do anything meaningful without being able to type in my password.

My best bet iis to fix the keyboard issue then change my /etc/network/interface file. The keyboard is just a basic Dell USB mouse and keyboard. It is the cheap pair they send with the PowerEdge servers. I know it is not the keyboard because it works in BIOS and I get a light on it when Mythbuntu is running, I have also used it on other PCs. Also lsusb  lists it as  Dell Keyboard (maybe not verbatim). I have tried other keyboard and nothing. I also tried a few Logitech all in keybaord (K400 and TK820 I believe are the models numbers) that use the same USB dongle. The mouse functions work but the keyboard doesnt. I have tested on every single USB port. I played around with some USB settings in the BIOS and nothing.

I checked to see if I could boot into the terminal but I cant seem to do it without editing files in the OS before rebooting. I've got a catch 22 as I see it right now but I sure I have missed something. 

Thanks in advance.

---

