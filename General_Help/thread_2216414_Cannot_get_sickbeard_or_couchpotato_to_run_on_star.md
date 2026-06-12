---
title: "Cannot get sickbeard or couchpotato to run on startup on ubuntu server 12.04LTS"
date: 2014-04-11
forum: General Help
---

### Post by darren10 on 2014-04-11
[COLOR=#333333][FONT=UbuntuRegular]I know this question has been asked dozens of times, though nothing I read & try seems to be working for me.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My most recent problem was rebooting my machine to find sickbeard & couchpotato didn't start, and after manually starting them found they both lost all their settings. I fixed this issue on Couchpotato (no idea how...) though not on sickbeard.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So i removed everything to do with sickbeard. I removed my .sickbeard folder, init.d and default files and started again.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I followed this [tutorial to install sickbeard on ubuntu server]("http://vassie.me/installing-sick-beard-on-ubuntu-server/"). I followed it to the letter, only changing username to my own username.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]If i RDP into my box (which is how i do my install etc) and, via the terminal, type: sudo /etc/init.d/sickbeard start sickbeard fires up, so i can safely assume the init.d script is working.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Yet it will not run on boot.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]If i look in webmin at the boot and shutdown section I can see an entry for sickbeard. It tells me it is set to start on boot, and that it isn't running.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Can anybody please point me in the right direction to correctly get this thing to run when my box reboots.[/FONT][/COLOR]

---

