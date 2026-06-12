---
title: "problem with Nvidia GeForce4"
date: 2007-04-25
forum: General Help
---

### Post by darkenemy on 2007-04-25
I have an Nvidia GeForce4 graphics card.  i have gotten it to work on my windows machine, but have so far been unable to install the drivers necessary (i think)

when i got the driver from Nvidia, and i tried to configure the X thing, i got these errors

 You do not appear to have an NVIDIA GPU supported by the 1.0-9631   
           NVIDIA Linux graphics driver installed in this system.  For further 
           details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in 
           the README available on the Linux driver download page at           
           [www.nvidia.com](www.nvidia.com).

  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

  ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).



when i try to boot my feisty computer, there comes a blue screen that tells me essentially the the X server does not work (i *think* its x server)


can anyone help me get this damn card to work!

---

### Post by spankymasterc on 2007-04-25
do this in recovery mode...

sudo dpkg-xserver xorg and check if nvidia is in there.....

if u dont find it do this in recovery mode 

sudo apt-get install nvidia-glx

and it will install the drivers then do the first thing again

::cheers::

---

### Post by darkenemy on 2007-04-25
this is what i get in failsafe (is that what you meant by recovery?)

unas@unas-desktop:~$ sudo dpkg-xserver xorg
sudo: dpkg-xserver: command not found
unas@unas-desktop:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done

nvidia-glx is already the newest version.
The following packages were automatically installed and are no longer required:
  libportaudio2 libglib1.2 libgtk1.2-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by et voilà on 2007-04-26
the command is dpkg-reconfigure xserver-xorg

---

### Post by dagrump on 2007-04-26
Search for envy, I had the best luck w/ no gui, this gets your drivers & installs them. I keep reinstalling as I break things. Kinda like a bull in a china shop. I have had good luck with this fix.

---

### Post by flyboy284 on 2007-04-28
I just got my GeForce4 MX440 AGP8x card working today this is what I did:
I used the synaptic package manager to install the _nvidia-glx_ driver, then edited the xorg.conf file adding lines to make the Device Section look like this:
```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Option		"NvAGP"	"1"
	Option		"AllowGLXWithComposite"	"True"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"		"True"
	BusID		"PCI:1:0:0"
	Option		"UseDisplayDevice"	"DFP"
EndSection

```
[COLOR="Red"]Note:[/COLOR] I changed the _BusID from "PCI:0:5:0" to "PCI:1:0:0"_

If you can't get to a GUI do this:
on reboot press ESC key to get into the Grub menu
then _Select recovery mode_
then type this at the prompt:
```

nano /etc/X11/xorg.conf

```
(you may need _sudo_ in front of this command try without it first)
then add the lines under the Device section
And Hopefully it will work for you.
[COLOR="Red"]Note:[/COLOR] Make sure the driver line says _nvidia not nv,_ change to _nv _to get the the GUI if X server fails to start.

---

