---
title: "Xorg wont work with my ATI PCI-Express"
date: 2005-04-18
forum: General Help
---

### Post by GazaM on 2005-04-18
I'm completely new to Linux, so forgive me if any of this sounds stupid. I recently downloaded the Ubuntu 5.04 Live CD for AMD64 to test out on my new PC as I wanted to try it out before deciding whether I should fully install it. I got through most of the stages until it came to 'entering preinstalled session' and then it says failure, and gives me the choice to skip and come back. I then run the CD check and select the option again and it seems to work fine, until it comes to the black screen where it displays all of the processes being started, and when all that is done the xorg / xserver fails and then I'm just left at a console. I've come to the conclusion that it's my ATI X700Pro causing the problems as I've tryed a 32bit LiveCD on another computer with an AGP ATI 9600 and it works fine. I have searched around and found that PCI Express causes alot of people problems and the way to fix it is to install new drivers etc. but I can't as anytime I try to do anything in the console with sudo I'm asked for a password, and as far as I know there's none so it wont let me do anything, plus the fact that I'm not sure if this is possible on the Live CD as all solutions were for full installations! Any help is greatly appreciated as I really want to be able to run Ubuntu on my computer. By the way my system is MSI K8N Neo4 Platinum with AMD 64 3200+, SATA 200GB, ATI X700Pro, etc.

---

### Post by GazaM on 2005-04-25
Over 30 views and no reply! Surely someone has an idea how to help. After X-org fails to start it shows me a log and in that it says that neither a device or monitor was found! Could the fact that I'm using DVI make a difference? Should I use the VGA output instead?

---

### Post by stejorge on 2005-05-16
[QUOTE=GazaM]Over 30 views and no reply! Surely someone has an idea how to help. After X-org fails to start it shows me a log and in that it says that neither a device or monitor was found! Could the fact that I'm using DVI make a difference? Should I use the VGA output instead?[/QUOTE]

I have the same problem, tried both DVI and VGA output, but it did not help. Tried 32 bit and 64 bit version, same problem. Tried the 32 bit on my laptop, and it worked fine there ](*,)

---

### Post by giardino on 2005-08-03
sup.... i have the same prob my system is. 
Motherboard: DFI lanparty nforce 4
ATI radeon X800XL (PCI XPRESS)
OCZ 2X512 MB PLATINIUM ED
ATHLON 939 WINCHESTER 3200+ @ 2.6 Ghz

THE PROB IS THE VIDEO CARD... i have cheked some forums. and we have to configure our LANS (ip address, subnetmask, and default gateway) to enter to the internet and download the driver for our video cards. We have to do all this by commands and i only know how to configure the LAN.

1. first is to configure the ip address and its subnetmask:
- ifconfig eth0 <ip address> netmask <subnetmask> 
Example: ifconfig eth0 10.0.0.2 netmask 255.255.255.0

-route add -net default gw <default-gateway> dev eth0 
Example: "route add -net default gw 192.168.2.1 dev eth0" will add the route required for this computer for its gateway.

now u have your LAN configured....

Then i dont know how to connect to the internet by a browser to download the video driver. Wich i expect some please contiunue helping here cuz im Linux newbie.

---

### Post by Orborde on 2005-08-06
> Then i dont know how to connect to the internet by a browser to download the video driver. Wich i expect some please contiunue helping here cuz im Linux newbie.
My solution is to do it on another machine and then use a USB flash drive to move it over. Those are easy to use in command line.

---

### Post by Tuna13 on 2005-08-28
[QUOTE=GazaM]I'm completely new to Linux, so forgive me if any of this sounds stupid. I recently downloaded the Ubuntu 5.04 Live CD for AMD64 to test out on my new PC as I wanted to try it out before deciding whether I should fully install it. I got through most of the stages until it came to 'entering preinstalled session' and then it says failure, and gives me the choice to skip and come back. I then run the CD check and select the option again and it seems to work fine, until it comes to the black screen where it displays all of the processes being started, and when all that is done the xorg / xserver fails and then I'm just left at a console. I've come to the conclusion that it's my ATI X700Pro causing the problems as I've tryed a 32bit LiveCD on another computer with an AGP ATI 9600 and it works fine. I have searched around and found that PCI Express causes alot of people problems and the way to fix it is to install new drivers etc. but I can't as anytime I try to do anything in the console with sudo I'm asked for a password, and as far as I know there's none so it wont let me do anything, plus the fact that I'm not sure if this is possible on the Live CD as all solutions were for full installations! Any help is greatly appreciated as I really want to be able to run Ubuntu on my computer. By the way my system is MSI K8N Neo4 Platinum with AMD 64 3200+, SATA 200GB, ATI X700Pro, etc.[/QUOTE]
 coool, me got same problem with ati x700 pro pci-e card! tried teh exact same u did on my bro's 9600 card with the 32bit version adn it worked! been checking the forums and i find alot of xserver problems, alot of them mention trying vesa driver or radeon driver that comes along iwth ubuntu. i'mma see if anything works and get back to u guys later

---

### Post by IANRAL on 2005-08-31
[QUOTE=Tuna13]coool, me got same problem with ati x700 pro pci-e card! tried teh exact same u did on my bro's 9600 card with the 32bit version adn it worked! been checking the forums and i find alot of xserver problems, alot of them mention trying vesa driver or radeon driver that comes along iwth ubuntu. i'mma see if anything works and get back to u guys later[/QUOTE]
 Same problem with Matrox P650 card

---

### Post by 1inxs on 2005-09-03
The ubuntu forum reminds me of the old 14400 dial up modem days. It is extremely frustrating. You got to be shitting me!! This post was started back on  4/18/05 and still no one has figured out a fix for the ATI X700? All the insults flung at Microsoft and no fix for the ATI X700 PCI express after 4 months [-X  I'd say Windows is kicking the Linux world ass. I guess you get what you pay for.

---

### Post by Arne Caspari on 2005-09-05
I do not own a ATI X700 but I found something on the net: The xorg configuration needs an additional line: 

```
Option "MonitorLayout" "LVDS,AUTO"
```

But I am not sure how to add this line to the LiveCD :-(

Have you tried a Breezy Badger CD?

---

### Post by rafakl on 2005-09-06
i think its possible to edit the file, and then start the x server with the command "startx".

But the problem comes editing the file, because you must use one of that ugly text editors like vi.

BTW, the config file is in /etc/X11/xorg.conf

---

### Post by Oberkorn on 2005-09-07
Alright, alright, alright!

Fellow ATI X700/800 folks lol.  Same deal here.  X700 Pro.

I'm not sure how to edit the file on the cd.  I'm pretty sure that you cannot because you can't write to it but I'm just guessing.

To do it on the install version, you would just enter:
sudo nano /etc/X11/xorg.conf
<password>

Now the question is:  where do you put the following in the .conf file?
Option "MonitorLayout" "LVDS,AUTO"

Thanks and hopefully we'll all figure this out together!!!

---

### Post by Oberkorn on 2005-09-07
Oh and another thing:  putting "vesa" in place of "ati" doesn't work for me.  It actually causes a black screen.

I end up having to reboot, go to recovery, and remove it.

Might just be me.  Seems rare as most of the folks on this forum and elsewhere say to do that.

---

### Post by Arne Caspari on 2005-09-07
[QUOTE=Oberkorn]
To do it on the install version, you would just enter:
sudo nano /etc/X11/xorg.conf
<password>

Now the question is:  where do you put the following in the .conf file?
Option "MonitorLayout" "LVDS,AUTO"[/QUOTE]

Put it in the "Device" section. ( Ie. look for the section named: 
```
Section "Device"
```

If this does not work, try: ```
Option "MonitorLayout" "LVDS,TMDS"
```

---

### Post by Tuna13 on 2005-09-12
HEY! I'm back and learned something NEW! LoL. apparently the week when i posted i didn't even know how to change directories (XD) but yeh, i'm gonna try waht u guys suggested. lol. the vesa thing didn't work for me either! was gonna post earlier, sorry if u tried it and it messed up ur screen. good luck trying to find a solution. i'll post again if it works.

EDIT: It didn't work. sniffles

---

### Post by cornix on 2005-09-26
For those who are new to debian/ubuntu, it might help to point out that any installed package can be reconfigured dpkg-reconfigure "package"..

So to configure xorg, you should open a new terminal (ctrl-alt-F1), run ```
sudo dpkg-reconfigure xserver-xorg
```

To just get a graphical user interface, select the "vesa" driver. Make sure you select a screen resolution supported by both the monitor and the graphics card. 1024*768 is a good bet. If vesa does not work, try "ati" instead..

After getting your xserver up and running, you should download and install the correct driver from [www.ati.com]("http://www.ati.com")

---

### Post by victor_c26 on 2005-12-01
How do you do this on the live cd though. I've been trying to use the live cd for a couple of months now with no luck.

Is there a command that I have to enter at the boot screen in order to beable to edit the xorg.conf file. I know what to do in order to edit the file so ubuntu uses the VESA drivers, but when I try to run the live cd, it just loads the OS without even giving me a choice as to which graphical driver I want to use.

I'm really close to giving up on linux all together guys. It's a shame really, it feels like a great OS, but damned if the ati issue isn't incredibly frustrating.

I'm writing this post on Ubuntu right now on an old laptop with the live cd running, and also installed Ubuntu on an old computer I have (Old Celeron with 128 MB of RAM). But I'd really like to use the live CD on my most powerful rig (Athlon 64 3500+ Venice core with 1 GB of DC DDR RAM). But it happens to have an ATi card. I'm still rather surprised this hasn't been fixed a long time ago, both on the ATi front, and the Ubuntu front.

Instead of using the ATi drivers that come packaged in the live CD, why not switch the xorg.conf setting to VESA upon detecting an ATi card?

---

