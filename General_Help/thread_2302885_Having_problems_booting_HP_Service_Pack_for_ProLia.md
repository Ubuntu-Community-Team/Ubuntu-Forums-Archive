---
title: "Having problems booting HP Service Pack for ProLiant (SPP) Version 2015.10.0"
date: 2015-11-14
forum: General Help
---

### Post by superandyjamieson on 2015-11-14
Hey guys,

I can't seem to get the [HP Service Pack]("http://h17007.www1.hp.com/us/en/enterprise/servers/products/service_pack/spp/index.aspx") to fully boot, I can get to the options menu (Automatic mode and Interactive mode) and no matter what option I select it [([http://i.imgur.com/Cjol1gX.jpg](http://i.imgur.com/Cjol1gX.jpg)) and then loads [this environment]([http://i.imgur.com/M6GWSmR.jpg](http://i.imgur.com/M6GWSmR.jpg)) I can move the mouse cursor but noting else happens. I used HP's USB key utility to make a bootable USB from Service Pack ISO, I'm trying to update the firmware on my P410 Raid Controller, this is housed in a Ubuntu based HP N54L.Checksum is correct, ISO size is 5.12GB, I'll need to track down a DL DVD :/Google has turned up nothing for me, any help would be greatly appreciated!Cheers!"]loads this screen]("http://Hey guys,I can't seem to get the HP Service Pack to fully boot, I can get to the options menu (Automatic mode and Interactive mode) and no matter what option I select it [loads this screen) and then loads [this environment]("http://i.imgur.com/M6GWSmR.jpg") I can move the mouse cursor but nothing else happens. 

I used HP's USB key utility to make a bootable USB from Service Pack ISO, I'm trying to update the firmware on my P410 Raid Controller, this is housed in a Ubuntu based HP N54L.

Checksum is correct, ISO size is 5.12GB, if I can't get the USB to work I'll need to track down a DL DVD :/

Google has turned up nothing for me, any help would be greatly appreciated!

Cheers!

---

### Post by superandyjamieson on 2015-11-20
[FONT=arial]Another route could be using the .rpm files, I've tracked down the files I need to use for the Raid card on the disk image. According to a few other posts you can convert them to .deb, I'm just not sure if this would be the best method.[/FONT]

---

### Post by superandyjamieson on 2015-11-29
Managed to solve it, you can see how here - [https://www.reddit.com/r/sysadmin/comments/3u04jo/cant_boot_hp_service_pack_for_proliant_to_update/](https://www.reddit.com/r/sysadmin/comments/3u04jo/cant_boot_hp_service_pack_for_proliant_to_update/)

---

