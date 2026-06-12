---
title: "ATI restricted drivers + reboot = black screen (8.04)"
date: 2008-04-25
forum: General Help
---

### Post by Ferux on 2008-04-25
Hi, i have this problem:

After a fresh Ubuntu Hardy Heron install, it's no problem to boot in Ubuntu. The system then asks me to install proprietary ATI drivers (and I want these to run compiz). After installing the drivers, I reboot. Ubuntu shows it's loading bar, but after that's complete, I only see a black screen. It doesn't do anything anymore.



Ubuntu Hardy Heron x64 desktop
MOBO: MSI K8N Neo2 Platinum
PROC: Athlon 64 3500+
MEM: 1GB
GRAPH: ATI 2600XT on AGP
SCREEN: Samsung 2232BW (22")

Does anyone see a possible sollution to this?

Many thanks

---

### Post by pro003 on 2008-04-25
yeah buddy, I had exactly the same problem - but in 7.10! Now with Hardy there's no such problem and I got 2600 pro too. That was annoying in Gutsy but now everything works fine with proprietary driver. 

try reboot and select from grub menu 1 upper option but type 'e' and than in the next menu select one of those options by typing letter 'b' (boot)...

if you still get black screen at startup I would recommend you to reinstall the system and than before installing proprietary driver make those things like sudo apt-get update and enable repositories, etc. Then open restricted manager and sheck the 'enable ati adriver'...

I hope someone will give you better idea...

good luck

---

### Post by Ferux on 2008-04-25
That doesn't solve the problem, thanks for the answer though.

---

### Post by gmrishel on 2008-05-06
I had the same problem, plus  more.  When I have the ASUS  AH2600PRO installed, Hardy does not see my wireless card.  When I enable the restricted drives and reboot I also get a black screen.  Frustrated I reinstalled Hardy with the NVIDIA geforce 5200 card.

---

### Post by shakabra on 2008-05-07
When you get to the black screen press ALT+F2 you won't see anything but type "metacity --replace" with out the quotes and press enter.

---

### Post by MaindotC on 2008-05-07
Also the xorg.conf file is backed up each time it is modified.  If you press alt + f2 then go to /etc/X11 you'll see a bunch of xorg.conf files in numerical order.  Backup the current xorg.conf:

```

sudo mv xorg.conf xorg.conf.backup

```

Then move one of the numbered xorg.conf's as the actualy xorg.conf:

```

sudo mv xorg.conf.1 xorg.conf

```

Restart your x-server by pressing ctrl + alt + backspace and tell us if you still have a black screen.

---

### Post by pro003 on 2008-05-07
YOU CAN ALSO GET IN SAFE TERMINAL MODE OR REPAIR MODE FROM GRUB MENU AND:

```
sudo aticonfig --initial -f
```

---

### Post by cerebellum on 2008-05-08
I had this problem too, solved it by restart and get into recovery mode, select repair x server. Seems to work.

---

### Post by tosoth on 2008-05-08
> **cerebellum said:**
> I had this problem too, solved it by restart and get into recovery mode, select repair x server. Seems to work.

I think this "repair" turns off proprietary ATI driver, thats why black screen is gone, but it doesn't solve the problem, as ATI driver still doesn't work.

---

### Post by cerebellum on 2008-05-08
> **tosoth said:**
> I think this "repair" turns off proprietary ATI driver, thats why black screen is gone, but it doesn't solve the problem, as ATI driver still doesn't work.
Now that u mentioned it, I notice that the ATI driver is said to be in use, but the check box is not checked.
However, I can still get my screen resolution working with my widescreen (which didn't work before: [http://ubuntuforums.org/showthread.php?p=4911821](http://ubuntuforums.org/showthread.php?p=4911821))

---

### Post by MaindotC on 2008-05-08
I'd like to know what Ferux thinks of all this.

---

### Post by Dmitrys on 2008-06-14
Hello! 

I've exactly the same problem with Radeon 1950 Pro (AGP) + Samsung SyncMaster 226bw (22") after enabling restricted ATI driver - getting Black screen after Reboot. ](*,)

Tried to do a manual driver installation, but still getting the same result. Now I am: :-#

Any help will be appreciated! 

Thanks :)

---

### Post by bufsabre666 on 2008-06-16
if its blank and takes like 10 minutes to boot with no boot screen its not broken, when it gets to the OS log on, open a terminal

```
 sudo apt-get update && sudo apt-get install startupmanager
```

it will then be under the system->administration folder, set the boot screen to something descent ((i like 1024x768 at 24 bit myself)) and restart, it should restart with a boot screen and faster

ive been through this problem on 3 different computer one with nvidia one with ati and the other with intel so its a pretty universal problem, but this is the only solution ive found to this, but it works so who cares right?

---

### Post by AndrooUK on 2008-07-15
Yeah I have this same problem too!

It's hit and miss whether it will load the login screen or stay blank and do nothing.

Restarting, pressing ESC to open the boot menu, and choosing recovery mode, then resume normal start seems to work for me.

Repairing the X-server does indeed disable the ATI drivers.  Damn ATI!

I've just found Compiz and want to keep it!  Can't do anything graphical without the drivers... wish ATI would make better ones for Ubuntu/Linux!

If anyone knows of a fix/better driver, that'd be cool.  Disabling usplash doesn't help either...

---

### Post by pro003 on 2008-07-15
I found that it's best to install fglrx from restricted driver manager and quit messing around with ati's drivers... they annoy me! last two versions I even didn't try to install, although I regularly download them :lolflag:

---

### Post by zeav on 2008-07-26
> **Dmitrys said:**
> Hello! 

I've exactly the same problem with Radeon 1950 Pro (AGP) + Samsung SyncMaster 226bw (22") after enabling restricted ATI driver - getting Black screen after Reboot. ](*,)

Tried to do a manual driver installation, but still getting the same result. Now I am: :-#

Any help will be appreciated! 

Thanks :)

I've got a Radeion 1950 Pro (AGP) too, with a Samsung SyncMaster 245b (24"), after I enabled the restricted driver I am getting black screen after the Ubuntu loader, and when Im going in rescue mode I repair x-server, and I can use the login menu. But after that it's just white. Even in safe-mode, only terminal that works.

Someone, please help?

---

### Post by cavehomme on 2008-08-02
> **zeav said:**
> ......after I enabled the restricted driver I am getting black screen after the Ubuntu loader, and when Im going in rescue mode I repair x-server, and I can use the login menu. But after that it's just white. Even in safe-mode, only terminal that works. Someone, please help?

Come on guys, what kind of support - community or otherwise - is it when someone facing a major issue like this has to wait a week and still no help!

This major problem with the ATI driver, i do understand that it is one which is simple to resolve by ATI or Ubuntu people by fixing some  issues in the code or config file. 

Most of us here are linux newbies, although we might be very experienced computer users coming from the Microsoft world. I have nearly gone back to XP due to these ubuntu frustrations - mainly lack of adequate quality control, version control, poor support when it really matters.

By the way I have exactly the same issue and ended up having to re-install 8.04, there was no way of recovery that i could find. Extremely frustrating, and I do not want to faff around with config file changes and risks screwing up something else. 

:confused:

---

### Post by SamTzu on 2008-08-02
I have now been up 12hours straight with this issue ones again.

Hardware/OS - ATI X1900/AMD 64bit with Ubuntu 8.04 LTS 32bit version. 
Here is my xorg.conf that works for me (though slowly)
The resolution for my dualhead ATI is 1600x1050 x 2 (extended desktop)
/etc/X11/xorg.conf
------------------------------------------------------


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
#	Identifier   "aticonfig-Monitor[0]-1"
#	Option	    "VendorName" "ATI Proprietary Driver"
#	Option	    "ModelName" "Generic Autodetecting Monitor"
#	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
#	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	Identifier "aticonfig-Screen[0]-1"
#	Device     "aticonfig-Device[0]-1"
#	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by SamTzu on 2008-08-03
Had to give up ATI drivers. I just could not get them to work. Something odd in KDE4.1 shows my dualhead two different desktops for a few seconds right after logging in but then "something" turns the display in to a "clone" displays that shows the same destop on both screens.

Any ideas what could cause this?

---

### Post by h0lix on 2008-08-20
i found this thread when i was trouble shooting the exact same problem on gutsy. one of the first things i did when i got the fresh install up was install my proprietary drivers for my ATI card. I noticed that shortly after i did this X would crash and give me a totally black screen.

i changed the default theme to more simple theme that didnt use the fluid window graphics (ie, smooth mac-like minimizations etc)

for whatever reason, after i did this i was able to continue to use my machine without a crash. 

if you change your theme to something that doesnt use all the unnecessary graphics you will be able to use your machine to diagnose the problem. i used crux.

i know this isnt a total fix, but it should allow you to stay out of safemode and give you a gui to work with it.

hope that helps.

---

### Post by baddelini on 2008-08-20
So I was having this same problem too. (And created an account to bring you my solution.)  I activated the restricted drivers and bam, black screen after loader.  Then I would try the 'x-server fix' and would have a white screen after login.  

Rejoice people, there is a fix.  Though the only way I know of is if you have Envy/EnvyNG installed and used it for your drivers.

What I did was boot in safe mode, then dropped down to root.  Then I punched in
```

$ nano /etc/X11/xorg.conf

```

And then find, under the section for your video card, where it says 'Driver'  It'll be pointing to the fglx or whatever its called that breaks my **** all the time.  Well I changed that, don't think it matters what to, but I did it to 'radeon'.

On reboot I had a login screen and then after that the damn white screen.  So I got into terminal (CTRL ALT F1) and ran the text version of EnvyNG.

```

$ EnvyNG -t

```

Ran through that, rebooted, and got right back to normal.  So if you're lucky enough to have envy, or able to get to the white screen and run the commands to download and install it, there's a workaround so you don't have to reinstall.


Good luck!

---

### Post by Tsingi on 2008-08-21
I've had no end of grief from my ATI card screwing up my system, I think the fix is to spend $40 on an NVidea card.

This is unfortunate because 

     A: I'm Canadian and so is ATI. 
     B: The Mach cards worked so well with Linux historically.

I don't even want to know if it gets solved, I expected big things when AMD bought ATI, I'm very disappointed, and they aren't worth any more of my time.

I'll give the card to someone who uses windows where it is supported.

-- 
A disgruntled Tsingi.

---

### Post by stoopidnewb on 2008-08-23
I have tried everything I know how to try to get these drivers installed and functional.  Tried several different methods from serveral different sources to no avail  including envyNG.  I have run out of ideas and patience.  Makes me wonder why ATI releases software that does not work.  I know if they don't get it together quick, I will no longer be an ATI/AMD customer.  I don't care if Ubuntu or ATI makes the drivers but, come on, we need something that works.  Everything else seems to work ok except these drivers.  Why is that so much more difficult?  I will just have to put up with low quality video until I consider weather I will pay 200 bucks for Windows and scrap Ubuntu or for an nvidea card.  \

Any one who has an nvidea card that works, can you please tell me which one and what you did to make it work.  preferably comparable or better than my current one.  
currently using
Radeon X1950 pro

BTW if you want to test the ati drivers, use Envy NG didn't work for me just like everything else didn't but at least I didn't have to reinstall the whole system.

If you get a black screen press esc while restarting to get to GRUB menu.

choose the one that says something like safe mode or restore mode

choose repair x drivers

reboot(can do this by simply typing the command "reboot" without quotes)

After I did this I got to my login menu, but logging in normally got me a white screen instead of a black one.

If this happens, restart and go to safe mode under the options in the login menu

open envy ng and select uninstall ATI drivers.  It looks like when it does this, it uninstalls the ATI drivers and reinstalls the original ones that came with Ubuntu that work but don't allow advanced graphics.  This leads me to believe that maybe, if you have this program installed, it may be a usefull tool to restore your comp if you try to install the ATI drivers in a different way.  Haven't tried it yet.

Hope this helps everyone that is going through what I did

---

### Post by Liviu-Theodor on 2008-09-02
> **Ferux said:**
> Hi, i have this problem:

After a fresh Ubuntu Hardy Heron install, it's no problem to boot in Ubuntu. The system then asks me to install proprietary ATI drivers (and I want these to run compiz). After installing the drivers, I reboot. Ubuntu shows it's loading bar, but after that's complete, I only see a black screen. It doesn't do anything anymore.



I have an older Radeon 9500 (256 bit), but I have enabled Compiz with the open-source drivers with no problem. Still, I am not using Ubuntu 64 bit, because the processor is a 32 bit AMD Athlon 2600+ (Barton technology).

A solution for your problem could be: boot in ubuntu safe mode, and run the command:
```
sudo dpkg-reconfigure xorg.conf
```

---

### Post by Ferux on 2008-09-05
**Nevermind this, watch post below for the solution**

[i]After 4 months, and trying everything suggested in this thread, there is still no solution to the problem. I think that's very sad.

I managed to get the white screen, and even to boot again in the safe gnome session (option at login), but that's not a solution since I want to use Ubuntu in full effect, with compiz-fusion, accelerated video.. Installing Ubuntu again is not an issue.

I have no other option than to go BACK to Windows XP. I can't afford to spend another &#8364;100 just because I want to use this beautiful *free* OS (which I like much better than Windows and which I'm addicted to).

I will use XP till the moment there's a fix for this problem. If there will ever be a fix..

PS, at Liviu-Theodor: I used Ubuntu 64 with my Radeon 9800 Pro with succes, but the fan on the card broke down. I replaced it with this 2600XT which gives me all the trouble right now.[/i]

---

### Post by Ferux on 2008-09-07
Good news for the people suffering this problem. In a last attempt, I found the - very simple - solution.

1. Ati released a new driver for the card which can be downloaded from their site.

2. sudo sh file-of-the-driver.run

3. Reboot - maybe this is not necessary

4. sudo aticonfig --initial

5. Reboot and enable compiz-fusion :guitar:

---

### Post by solarwind on 2008-09-08
> **Ferux said:**
> Good news for the people suffering this problem. In a last attempt, I found the - very simple - solution.

1. Ati released a new driver for the card which can be downloaded from their site.

2. sudo sh file-of-the-driver.run

3. Reboot - maybe this is not necessary

4. sudo aticonfig --initial

5. Reboot and enable compiz-fusion :guitar:

Messes up things just the same. I'll have to try envy.

---

### Post by solarwind on 2008-09-08
Had exact same issue. Fixed problem by installing and running envy-ng.

---

### Post by rmjohnson144 on 2008-09-15
> **Ferux said:**
> Good news for the people suffering this problem. In a last attempt, I found the - very simple - solution.

1. Ati released a new driver for the card which can be downloaded from their site.

2. sudo sh file-of-the-driver.run

3. Reboot - maybe this is not necessary

4. sudo aticonfig --initial

5. Reboot and enable compiz-fusion :guitar:

This is what worked for me and what is listed on the ATI website.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat88-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat88-inst.html)

however it says to skip the reboot of step 3 and run aticonfig first.

a big thanks
-=Mark=-

---

### Post by picciano on 2008-09-21
New ATI drivers are still not working with my Radeon 9600. This is silly, is there any "good" way to set up video that just plain works?

---

### Post by pro003 on 2008-09-22
I have this flickering when playing video but in a full screen mode everything is fine. I guess that's some conflict with compiz fusion...
but hey, can't have it all!

---

### Post by rmjohnson144 on 2008-09-22
I think it's just immature drivers still.  After a lot of 3D testing and finding out all have issues I decided to swap out my 3870 for my 88ooGT and all is fine now.

Hopefully drivers are sorted out soon.
-=Mark=-

---

### Post by mziskandar on 2008-09-23
Mine is cooler.. a white blank screen and a little mouse arrow. Desktop seems exist behind that white blanket. I will post the solution if I get one..

---

### Post by thebigredone on 2008-09-27
i also have this, it is very annoying. First i install the drivers, reboot and get the black screen, then i hardcrash the comp, reboot in recover mode, fix the Xserver and startup. Try to enable visual effects and i get the white screen.

---

### Post by rmjohnson144 on 2008-09-27
The trick I did was reboot and go into grub and tell it to boot in recovery mode and it fixed itself there.  then just reboot normal and all was fine.

Good luck
-=Mark=-

---

### Post by thebigredone on 2008-09-29
ive tried that, but i cant enable visual effects, and next time i reboot after that i go into low grafics mode

---

### Post by rmjohnson144 on 2008-09-29
> **thebigredone said:**
> ive tried that, but i cant enable visual effects, and next time i reboot after that i go into low grafics mode

actually, I uninstalled the drivers and used ENVY to install the drivers before that worked.  Not sure what method you used for installation.  although, I don't think I enabled the Visual Effects until after reinstalling mt 880GT as the ATI drivers were giving me problems in most games.  But movies play the same on both the 3870 and 8800Gt the same.  They play fairly well, but they still don't play 100% smooth.

-=Mark=-

---

### Post by Isilion on 2008-10-18
Hi. A week ago i posted a similar thread called "Imposible to get working ati 9800 pro" or something else. no replys. It shows some conf too. 
Personally I think there's no short time solution for this issue. after googling and googling, all points to that the ATI driver just simply SUX.
Reading this thread ive noticed that my model isnt the only affected by this. 
So, whats next point? Contacting ATI and demanding them a decent working driver, I suggest.
Perhaps we're thousands of ATI-linux users that are no more than the forgotten ones.
Im starting to think in selling the videocard too to a windows user, and buying a Nvidia.
or
Ill try to contact ATI ...

---

### Post by Neo_The_User on 2008-10-18
OK here is how you do it

[COLOR="SeaGreen"]**_[SIZE="4"]PLEASE NOTE!!! DO NOT USE ENVY![/SIZE]_**[/COLOR]

```

wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run
sudo apt-get install build-essential fakeroot dh-make debconf dkms cdbs debhelper libstdc++5 linux-headers-$(uname -r)
sh ati-driver-installer-8-9-x86.x86_64.run --buildpkg Ubuntu/hardy
sudo gedit /etc/default/linux-restricted-modules-common

```

Add fglrx to DISABLED_MODULES in between the quotes

**_WHAT YOU MIGHT BE DOING WRONG_**

Just adding in 3 files instead of all of them except the .changes

**_FOLLOW THIS EXACTLY_**

```

sudo dpkg -i xorg-driver-fglrx_8.542-0ubuntu1_i386.deb fglrx-kernel-source_8.542-0ubuntu1_i386.deb fglrx-amdcccle_8.542-0ubuntu1_i386.deb xorg-driver-fglrx-dev_8.542-0ubuntu1_i386.deb fglrx-modaliases_8.542-0ubuntu1_i386.deb
sudo aticonfig --initial -f

```

Restart computer. :guitar:

The drivers are just fine. I got 2 monitors, full hardware acceleration, latest and greatest fglrx drivers, works like a charm.

My fglrxinfo

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.1.8087 Release

```

glxgears
```

15491 frames in 5.0 seconds = 3098.040 FPS
16869 frames in 5.0 seconds = 3373.683 FPS
17093 frames in 5.0 seconds = 3418.595 FPS
17215 frames in 5.0 seconds = 3442.834 FPS
16942 frames in 5.0 seconds = 3388.279 FPS
15547 frames in 5.0 seconds = 3109.255 FPS

```

I have gotten 18000+ frames in 5.0 seconds numerous times. Unusually slow this time.

Here is my xorg.conf

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by Isilion on 2008-10-18
Hi. I did everything Neo_The_User said. now system boots, thanx. but it continues to not being installed properly. when i use:

isilion@isilion:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

i got that response.

and

isilion@isilion:~$ glxgears
1418 frames in 5.0 seconds = 282.813 FPS
1339 frames in 5.0 seconds = 266.268 FPS
1880 frames in 5.0 seconds = 375.250 FPS
1560 frames in 5.0 seconds = 311.743 FPS
1480 frames in 5.0 seconds = 294.422 FPS
1400 frames in 5.0 seconds = 279.074 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 19591 requests (18786 known processed) with 0 events remaining.
isilion@isilion:~$ 

i think its too slowly. problem should be easy for sure but im not too deep in linux to know how. so please, answer :P. Xorg.conf looks exactly to Neo's one

---

### Post by Isilion on 2008-10-18
> **Isilion said:**
> Hi. I did everything Neo_The_User said. now system boots, thanx. but it continues to not being installed properly. when i use:

isilion@isilion:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

i got that response.

and

isilion@isilion:~$ glxgears
1418 frames in 5.0 seconds = 282.813 FPS
1339 frames in 5.0 seconds = 266.268 FPS
1880 frames in 5.0 seconds = 375.250 FPS
1560 frames in 5.0 seconds = 311.743 FPS
1480 frames in 5.0 seconds = 294.422 FPS
1400 frames in 5.0 seconds = 279.074 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 19591 requests (18786 known processed) with 0 events remaining.
isilion@isilion:~$ 

i think its too slowly. problem should be easy for sure but im not too deep in linux to know how. so please, answer :P. Xorg.conf looks exactly to Neo's one

Asking in ubuntu it was finally solved. All i had to do whas editing etc/modprobe.d/blacklist-local and add # at the beginning of the line, so it reads

#blacklist fglrx

saved&exit, reboot, and:

isilion@isilion:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
2831 frames in 5.0 seconds = 566.200 FPS
2974 frames in 5.0 seconds = 594.800 FPS
3012 frames in 5.0 seconds = 602.400 FPS
2965 frames in 5.0 seconds = 593.000 FPS
2888 frames in 5.0 seconds = 577.600 FPS
2859 frames in 5.0 seconds = 571.800 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 60324 requests (60323 known processed) with 0 events remaining.
isilion@isilion:~$ 

to see if its really working.


I love you ALL, Ubuntu Community.

---

### Post by Isilion on 2008-10-19
OHHHH DAMN!!!...

Well, having fixed the driver problem, i told to myself "why dont try compiz?"...

I installed compiz following this Howto:

[http://www.ubuntu-es.org/index.php?q=node/59970](http://www.ubuntu-es.org/index.php?q=node/59970)

(its in spanish, but sure you can understand what he's doing by the commands)

After the reboot everything goes well. When i change session to xfce4-xgl, desktop starts, but looks weird. Window titles has lost their resolution (inside the windows everything's fine).

when i hit Alt+F2 and type "compiz --replace"

windows change, but the weird look of the windows continues (the loss of resolution then affect to ALL (title + inside the windows).

the first time i supposed it will be fixed in the next step, but no.
when i hit Alt+F2 again and type "emerald --replace", resolution doesnt fix and after one or two minutes something happens and i get to the login session.

I was able to do a comprobation once. I opened console and typed "gflrxinfo" again. It showed all related to mesa, mesa indirect rendering, etc. For some reason, following the tutorial to install compiz uninstalled the ATI driver. At this point, and because i didnt had anything valuable inside the computer, y restarted the pc with the xubuntu 8.04 installation cd and reinstaled ubuntu. i did again what neo's said and edited the file to put the # again.

fglrx info shows that ati its properly installed and gears work.

(i tryed to reinstall compiz following the tutorial and the driver messed up again with mesa, so i reinstalled xubuntu again and then drivers, all ok again)

At this point im waiting for you what to do because i dont know.Thanks in advance.

---

### Post by Isilion on 2008-10-19
Hi again. drivers are properly installed on a fresh installation of ubuntu. gears work, but launching OpenArena or Compiz make system crash and i need to hard shutdown. I have registered at ATI site and submitted 3 tickets... all they have done till the moment is sending automatic replys, but you can tell them that that didnt resolved your problem and in theory, puts you in contact with a tecnician...

From here I do a call to ATI-Linux users with same problems, to submit tickts to ATI. Im sure (and perhaps you're sure too) that main problem is the driver, that just simply sucks. Fails at installs byself and fails to work. As I have seen googling, Im not the only person having problems.

Some portion of ati driver code is open source, but some not, because its property of 3rd partyes. Perhaps we could make pressure to them to liberate? :S


I will paste now the ticket i've submitted to ATI. perhaps you know whats wrong..


Type of Inquiry: 	PC support
Bus Type: 	AGP
Operating System: 	Linux X86
Other Operating System: 	 
Driver Version: 	 
Driver Version: 	CATALYST 8.10
Other Driver Version: 	 
Category: 	Linux Driver Feedback
Driver Version: 	CATALYST 8.10
Topic: 	Lockups and Hangs
Trade-up to product
(Trade-up FAQ): 	 
Have you moved since submitting the rebate?: 	 
Order number: 	 
Sub-topic: 	3D Applications
Multimedia Center Component: 	 
Multimedia Center Version: 	 
Media Center Component: 	 
Media Center Version: 	 
Other Multimedia Center Version : 	 
Other Promotion: 	 
Other Topic: 	 
Graphics Manufacturer: 	ATI Technologies Inc.
Vendor: 	Not Sure
Application: 	Other
Application Name: 	OpenArena (in example, but everything fails)
Product: 	Radeon 9800 PRO 256MB
Application Version: 	Xubuntu 8.04
Which retailer did you purchase your ATI card from ?: 	 
Offer/ Department #: 	 
Was this purchased over the Internet?: 	 
Other Retailer: 	 
Purchase Date: 	 
Rebate Amount: 	 
New Address
Street Address: 	 
Address 2: 	 
City: 	 
Country: 	 
Postal Code / Zip: 	 
Province: 	 
State: 	 
State / Province / Division: 	 
Postal Code: 	 
Zip: 	 
Summary: 	PC hangs
Details: 	Hi. After succesfully installed your driver, system hangs at launching 3d applications, like games (in example, open arena). i've submitted two tickets more, look for them.

while launching open arena, after intro menu its ok for a time, then hang and need to hard-shutdown.

isilion@isilion:~/Desktop$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.1.8087 Release

isilion@isilion:~/Desktop$ fgl_glxgears
Using GLX_SGIX_pbuffer
2843 frames in 5.0 seconds = 568.600 FPS
2840 frames in 5.0 seconds = 568.000 FPS

(dont you think its slow?)

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "es"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

BIOS related settings are AGP 8x Video Aperture Size 256 mb.

Im running a IBM P4 2.8 Ghz, 1.5Gb RAM DDR2, MAXTOR 80gb.

-Im starting to think 2 things:

-1st: Your driver installator was that doesnt work at all. Look at it. I had to follow these commands to install the driver:

wget [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run)


sudo apt-get install build-essential fakeroot dh-make debconf dkms cdbs debhelper libstdc++5 linux-headers-$(uname -r)

sh ati-driver-installer-8-10-x86.x86_64.run --buildpkg Ubuntu/hardy

sudo gedit /etc/default/linux-restricted-modules-common

(to add fglrx between marks "")

sudo dpkg -i xorg-driver-fglrx_8.542-0ubuntu1_i386.deb fglrx-kernel-source_8.542-0ubuntu1_i386.deb fglrx-amdcccle_8.542-0ubuntu1_i386.deb xorg-driver-fglrx-dev_8.542-0ubuntu1_i386.deb fglrx-modaliases_8.542-0ubuntu1_i386.deb

sudo aticonfig --initial -f

And reboot. PC starts succesfully, login succesfully on Xfce4. Stable in desktop, but just launch, in example, OpenArena, loads and shows menu for a while, then hangs.

ATI RADEON 9800 PRO works for me like a charm, but in windows xp. i had Spore running perfectly for hours. So it isnt broken or anything. so:

2nd: As I've been Googling i've noticed many (too many, believe me) users of linux with ATI card problems. So whats the problem? Cant you do a better driver? At least one that works?At least the installation? :(

---

### Post by cerbero626 on 2008-11-07
Hi,

on my machine the fglrx-8-10 driver compiles and installs fine, but then crashes at boot. kdm starts and complains about the Xserver configuration. The ttys are available, however.
If I configure xorg /etc/X11/xorg.conf to use a different driver, such as vesa or ati, I am able to boot - but fglrxinfo segfaults.
Any Ideas? I went back to using fglrx-8-9 for the time being.

Greetz, Julian

Acer TM-292Lmi-M11; ATI Mobility Radeon 9700; Ubuntu/hardy; kdm, kde (Kubuntu);

---

### Post by bell1996 on 2009-09-27
After several hours of install, de-install, and troubleshooting, I finally found the solution.

I can't take take credit for the solution, because I found it here at [http://ubuntuforums.org/showthread.php?t=766699&page=5](http://ubuntuforums.org/showthread.php?t=766699&page=5)
by a post from "Isilion".

So here's what I did:

Installed the ATI drivers provided by at the [www.amd.com](www.amd.com) website:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.38&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.38&lang=English)

I have the Catalyst 9.2 version, but I think the latest version is 9.8 or 10.0 (I need to upgrade mine). Just download the latest version available.

Just follow the installer instructions. Installation application begins when you issue the following command:

sudo ./ati-driver-installer-9.2-x86_64.run

Take the defaults and it should only take about 1-2 minutes at most.

Don't forget to issue the last command: sudo /usr/bin/aticonfig --initial

Now it'll ask you to Re-boot. DON'T!! You have one other step to do.

Edit the following file (using your favorite editor. i use gedit)

sudo gedit /etc/modprobe.d/blacklist-local

Now comment out the one line but adding a "#" in front. It should look like this:

#blacklist fglrx

Now save.

Now reboot.

All should be good.

---

