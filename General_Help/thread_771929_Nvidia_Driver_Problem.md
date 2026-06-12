---
title: "Nvidia Driver Problem"
date: 2008-04-28
forum: General Help
---

### Post by ericf88 on 2008-04-28
World of Warcraft was running ridiculously slow for me so that gave me incentive to update my video driver and since I use an Nvidia card, I decided to use Envy to update my drivers. Everything seemed fine and the autodetect on Envy got my card right and did everything as if it was running fine and told me to reboot right after it finished. I reboot and get to the login screen with no problems. However, the minute I log in the screen goes white and doesn't do anything else.

My card's an Nvidia Gforce 9800 Pro and Envy seemed like it knew what it was doing so this seems completely random to me. If anybody has any adivce on how to fix this or at least revert it back to some manageable form of my Ubuntu, that'd be great. Also I'm using Ubuntu 8.04.

---

### Post by ryanhaigh on 2008-04-28
The fact that it works prior to logging in would indicate a problem with compiz to me, once you login leave it on the white screen and wait for login sounds to finish, press alt-f2 which will bring up the run dialog (even if you can't see it) type metacity --replace. That should replace compiz with gnomes default metacity window manager. You can then try and figure out what is causing the problem with compiz, or just disable it for the time being.


Alternately login then press ctrl-alt-F1 to change to a terminal, login and do killall compiz.

---

### Post by ericf88 on 2008-04-28
Ok, the first method worked and I can now see my desktop. What would be my next course of action to diagnose what happened?

---

### Post by ryanhaigh on 2008-04-28
I know compiz and the nvidia driver don't get along if Composite is enabled, you have to specify Option Composite Disabled somewhere in xorg.conf, but Im not on my ubuntu system now so I can't tell you where exactly it goes, goolge/forum search should help.

---

### Post by ericf88 on 2008-04-28
Ok, I purportedly disabled Composite by using [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) then rebooted, then reupdated my drivers with Envy again only to get the white screen again. I figured the Feisty guide would suffice since I couldn't find a proper Hardy guide.

---

### Post by Mr Frosti on 2008-04-28
The white screen could be a Compiz specific issue, or it could indicate a larger issue resulting from your nVidia driver upgrade. Envy makes a best attempt at installing and configuring your system, however in the event that building a module fails, I am not sure that it takes the correct actions in all cases. 

At this point, you might want to look into your "/var/log/Xorg.0.log" file and look for lines beginning with "(WW)" warning, or "(EE)" error. 

You can manually start Compiz running "compiz.real --replace" inside a terminal. If your screen goes white, terminal Compiz using the instructions above in this post.

---

### Post by ryanhaigh on 2008-04-28
> **ericf88 said:**
> Ok, I purportedly disabled Composite by using [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) then rebooted, then reupdated my drivers with Envy again only to get the white screen again. I figured the Feisty guide would suffice since I couldn't find a proper Hardy guide.

Can you check the xorg.conf file to make sure that envy has kept that configuration option. Also I'm not sure that site is the best choice considering its for an ati card. 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by ericf88 on 2008-04-28
I checked the Xorg.conf after the driver update and it seems Envy turns it on. I switched it off and rebooted; now everything seems fine at the moment.

---

### Post by dage on 2008-04-28
I think the best way to install your driver is do it manually, not through an automatic program like "envy" or "hardware drivers".
I've a Nvidia 8400 GS. Neither envy nor Hardware Drivers could resolve my display prob. I just had to install the binary driver and everything work without any trouble.

---

### Post by ericf88 on 2008-04-28
I did a little bit of a digging but could not find a guide for Binary Nvidia Driver installation because the Envy installation, even though it no longer produces the white screen, hasn't resolved the WoW issue and it's made it unplayable for me because my card can't even render as I found out using this test "glxinfo | grep rendering" and it returns a "No."

---

### Post by dage on 2008-04-28
if you have a nvidia card then you can go to [www.nvidia.com](www.nvidia.com) to download the driver, there is also an explication how to install it on the website :)

---

### Post by ryanhaigh on 2008-04-28
> **dage said:**
> if you have a nvidia card then you can go to [www.nvidia.com](www.nvidia.com) to download the driver, there is also an explication how to install it on the website :)

Of course there is no guarantee that this will fix the issue. 

A google search for wine nvidia wow brings up the gentoo wiki page with hints on how to get best performance (some thigs are not applicable because its gentoo) [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine), adding low fps brings up a number of threads where people have had problems eg [http://www.nvnews.net/vbulletin/showthread.php?t=110521](http://www.nvnews.net/vbulletin/showthread.php?t=110521) and they were using the driver from the nvidia site.

There is also the ubuntu wiki page [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) which has a link for troubleshooting.

---

### Post by dage on 2008-04-28
> **ryanhaigh said:**
> Of course there is no guarantee that this will fix the issue. 

A google search for wine nvidia wow brings up the gentoo wiki page with hints on how to get best performance (some thigs are not applicable because its gentoo) [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine), adding low fps brings up a number of threads where people have had problems eg [http://www.nvnews.net/vbulletin/showthread.php?t=110521](http://www.nvnews.net/vbulletin/showthread.php?t=110521) and they were using the driver from the nvidia site.

There is also the ubuntu wiki page [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) which has a link for troubleshooting.

I think binary driver is the best driver for your hardware because it's written by the manufacturer specially for your hardware.

There are never a method with 100% guarantee but i's better to give a try.

I've just bought I new PC with an NVIDIA 8400GS. Before installing the binary driver, I've tried many other methods like envy or "Hardware Drivers", nothing worked, I'd had to boot in safe mode all the time. Now, with the binary, everything work like an as.

---

### Post by genesis2seven on 2008-09-05
I have a similar set of issues with my 9800 series Nvidia cards along with others. See other post in Ubuntu forums:

[http://ubuntuforums.org/showthread.php?t=909460&highlight=Nvidia+9800](http://ubuntuforums.org/showthread.php?t=909460&highlight=Nvidia+9800)

Done a lot of looking around on the web and I've found rumors in a few other forums that there is a 177 beta version driver from Nvidia that works much better that two previously listed but haven't found any instructions on install.

---

