---
title: "I need a lot of help."
date: 2006-12-08
forum: General Help
---

### Post by Rxq on 2006-12-08
Using ubuntu.

I just switched from windows to ubuntu and it took be around 5 hours just to install the OS and figure out how to get online with my wireless router to ask questions.

1.  The screen is iiregular.  The sides are curving inwards give my desktop a hourglass look.  How do i fix this?  I tired change the resolution and got little success.  The Windows and Bars etc are all too big.  So is the general font.  Is there a control panel some where so i can change it?

2.  How do i remove the login menu so the password and account is not required every time i restart?

3.  I have a pritner hook up to my computer. How do i install the drivers for the printer or get it working?  Or does Linux Ubuntu not require drivers to be installed for all common perpherals? (like my router drivers)
 
4.  Does linux support games for Windows?  Or do i have to start using an windows emulator now?  I only have 512 ram.  Is that enough to run WINE w/o slowdowns?

5.  How do i run .exe or other installers?

6.  I think linux disabled one of my cd drives.  I'm not using the live cd feature mode and it still wont let me take out my cd.  How do i get the cd out or open my cd drive?

7.  Just downloaded firefox.  Its a tar.gz.  I dunno what that is or how to run it.  How do i install it?  What is a command line?

Thanks.

Please just give me an answer to my questions instead of posting links to other treads with long faqs.  I dont have enough time to sift through it all tonight, unless i fix problem #1, making it easier for me to read the screen.

---

### Post by marc_c on 2006-12-08
Since you didn't provide a lot of information on your setup, I can only guess that number 1 is being caused by the default video driver.

A good place to start would be looking the Ubuntu Starter Guide ([http://ubuntuguide.org/wiki/Ubuntu_Edgy)](http://ubuntuguide.org/wiki/Ubuntu_Edgy)).  Among it's many tidbits, it offers easy to follow instructions on how to install the correct drivers for ATI, Intel, and NVIDIA based graphics cards. There are also instructions on setting up your printer.

I will let someone else chime in on using WINE for Windows based games, as I am not a gamer.

Regards, Marc

---

### Post by Rxq on 2006-12-08
What kind of information do u need on my setup?
Im using a 64mb nVidia Geforce2 MX graphics card.

Adding on to question 6, i found an icon of my cd has been created.  I had to click on that icon and tell it to eject the disc to get the cd out.  why does this happen?

---

### Post by taurus on 2006-12-08
Because you need to unmount it before you can remove it.  That's how it works in Ubuntu or any other version of Linux.

---

### Post by Rxq on 2006-12-08
I still need an answer to number 1.

---

### Post by taurus on 2006-12-08
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install nvidia-glx  nvidia-settings
sudo nvidia-xconfig
```
Then, restart X with <Ctrl><Alt>Backspace.

---

### Post by ardvark71 on 2006-12-09
Hi...

Whew! Ok, I will help you with what I know although I don't guarantee it will solve your problems...

1. You didn't state what version of Ubuntu you installed so I went with Dapper on the instructions. You can follow this to download the Nvidia driver...

How to install Graphics Driver (NVIDIA) 
Read #General Notes 
Read #How to add extra repositories 
sudo apt-get install nvidia-glx nvidia-kernel-common (or follow Taurus's instructions above)
sudo nvidia-glx-config enable
Should the above not enable the new driver, you can enable it manually by opening the X config file: 
sudo gedit /etc/X11/xorg.conf
 
and replacing "nv" with "nvidia" 
Read #How to restart GNOME without rebooting computer 
Enable XvMC by creating the nVidia XvMC configuration file 
sudo gedit /etc/X11/XvMCConfig
Insert the following line into the new configuration file, to tell the players the name of the nVidia XvMC shared library: 
libXvMCNVIDIA_dynamic.so.1
To use XvMC to accelerate video playback, use the following flags. See [[1]] for more details. 
xine -V xxmc filename.ts
mplayer -vo xvmc -vc ffmpeg12mc filename.ts

This was from the Dapper unofficial starter guide wiki at:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

For Edgy, go here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

2. To my knowledge, you don't. This is how Ubuntu was constructed.
3. Most peripheral support with Ubuntu, I have found, is available out of the box. Just go to "System"--->"Administration"--->"printing" and configure your printer there.
4. 512 might be pushing it, especially with the newer stuff. Better off with at least a gig. With WINE, more the better. You might also want to consider Cedega, which is a flavor of wine that emphasizes gaming emulation.
7. Ubuntu already comes with Firefox. If you want to see if you can upgrade it, you can go into Synaptic and right click on the (Firefox) entry to upgrade.

Hope this helps.

Regards...

:KS

---

### Post by bg1256 on 2006-12-09
First of all, number 7: Firefox should come preinstalled, so you shouldn't need to install it.  But, on the weird chance it didn't, the easiest way would be to open up synaptic package manager, and search for Firefox there. Just check the box for firefox, then apply, and it will install automatically.

Second, I would visit [www.linux-gamers.org](www.linux-gamers.org) for questions related to gaming. I dual boot and don't do gaming in Windows, although I know it is possible. I just haven't had the time to configure everything.

---

### Post by Rxq on 2006-12-09
Im using ubuntu version 6.06 LTS for pc.

Thanks to thsoe who've helped! 
I got my pritner installed.

For problem #1 Its better now, but hte sides are still off and it still cives inward a bit.
AS for firefox, im trying to update it to version 2.  Currently its only 1.501
I downloaded the installer and unzipped it, but i cant install it.

Where are the program files kept?

---

### Post by budgie9 on 2006-12-09
You will probably find you need to use and re-set the monitor controls themselves. To get rid of the bends etc. Then you may find your resolution will need to be altered within Ubuntu, see the System - Administration tools Display I think. - Can't see it as I am in yuk, XP at this time. Here is a great source of info to start with and should answer some of your questions.   [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

---

