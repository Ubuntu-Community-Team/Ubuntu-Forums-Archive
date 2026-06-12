---
title: "Can't fix getting out of suspend for nvidia even with the official steps"
date: 2013-12-20
forum: General Help
---

### Post by michaeljj2 on 2013-12-20
[COLOR=#333333][FONT=UbuntuRegular]Even after doing the steps from Ubuntu Help for fixing the going out of suspend problem with nvidia cards, i still can make it work. When I wake up from suspend i get just black screen with blinking cursor and that's it....[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]below i'm pasting the steps i followed[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Suspend/Hibernation If you use an old NVIDIA driver, hibernation & suspend may not work, there is a workaround however.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]We need to edit xorg.conf, open a terminal and enter the following command:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]gksudo gedit /etc/X11/xorg.conf In the section called Section "Device" add Option "NvAGP" "1", you should end up with something like this:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Section "Device" Identifier "my id" Driver "my dr" VendorName "my vendor" BoardName "my board name" Option "NvAGP" "1" EndSection Blacklist the intel_agp module from being loaded by the kernel. This is done by editing blacklist.conf, open a terminal and type:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]gksudo gedit /etc/modprobe.d/blacklist.conf Then add the following line:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]blacklist intel_agp Reboot your system.[/FONT][/COLOR]

---

### Post by egeezer on 2013-12-21
For more help, we'll need to know:

Which version of Ubuntu you're running, which graphics card, and which Nvidia driver is enabled.

---

### Post by michaeljj2 on 2013-12-22
Right. 
13.10
geforce gtx 460
the nvidia-current from the app centre

thanks!

---

### Post by egeezer on 2013-12-22
No help here, I fear - I've not run 13.10 enough yet, and it doesn't have my favorite Nvidia fix, the jockey-text (backend of what used to be the Additional Drivers GUI).

I did install 13.10 server recently and put an Xfce desktop on it, so while you await actual help from people who do know what they are doing, I'll fire that up and see what I can do about it.

---

### Post by egeezer on 2013-12-22
Well, my kudged-up 13.10 system doesn't seem to have that problem (suspends okay, at least on a brief test).  

I just noticed, you followed directions for an OLD Nvidia driver, for an AGP card - yours is a much newer one (newer than mine, in fact) and it is a PCIe card - totally different animal.

My desktop is probably different from yours, but somewhere in your system is a Restricted Drivers GUI which will tell you what you are actually running.  I used Settings > Settings Manager > Additional Drivers to find it, though other desktops may have different names for the same general thing.  It turned out to be in Software and Updates, Additional Drivers tab.

Once you find that, try help.ubuntu.com/community to see if there is a fix involving your actual in-use driver.

---

### Post by egeezer on 2013-12-24
I just fooled around a bit with a Lubuntu 13.10 installation, and found it was able to suspend and return properly with the command:

```
sudo pm-suspend
```

On return (push Enter, for the most direct return) you will have the same screen when you left, terminal with ready cursor.

---

### Post by michaeljj2 on 2013-12-31
> **egeezer said:**
> I just fooled around a bit with a Lubuntu 13.10 installation, and found it was able to suspend and return properly with the command:

```
sudo pm-suspend
```

On return (push Enter, for the most direct return) you will have the same screen when you left, terminal with ready cursor.


thanks but that doesn't work for me, upon return the same happens as before :(

it sucks big time to not have suspend
how i'm going to fix that :(

---

### Post by michaeljj2 on 2013-12-31
> **egeezer said:**
> Well, my kudged-up 13.10 system doesn't seem to have that problem (suspends okay, at least on a brief test).  

I just noticed, you followed directions for an OLD Nvidia driver, for an AGP card - yours is a much newer one (newer than mine, in fact) and it is a PCIe card - totally different animal.

My desktop is probably different from yours, but somewhere in your system is a Restricted Drivers GUI which will tell you what you are actually running.  I used Settings > Settings Manager > Additional Drivers to find it, though other desktops may have different names for the same general thing.  It turned out to be in Software and Updates, Additional Drivers tab.

Once you find that, try help.ubuntu.com/community to see if there is a fix involving your actual in-use driver.

In additional drivers, i see that i'm using the 304 version of the driver and i'm given the option to choose 319 as well, should i do that?
 can it mess something?

---

### Post by michaeljj2 on 2014-01-01
bump for me

---

### Post by michaeljj2 on 2014-01-02
no one have tried?

---

### Post by pbrane on 2014-01-02
I would purge the nvidia drivers, reboot into nouveau and try re-installing the latest nvidia, 319 it seems for you.

If you want to try it you can install the drivers downloaded from nvidia. That's what I do. Basically you just login to a virtual term (CTRL+ALT+F2 for instance). kill lightdm, and run the nvidia installer with sudo. It will blacklist the nouveau driver and setup the xorg.conf file and even install the 32 bit libs if you are running ubuntu 64. And if you have dkms installed it will setup for kernel upgrades as well.

---

### Post by michaeljj2 on 2014-01-09
i installed 319 now and still can't suspend :(
everything else seems fine though.


is there anything else that can be done to have suspend?

---

