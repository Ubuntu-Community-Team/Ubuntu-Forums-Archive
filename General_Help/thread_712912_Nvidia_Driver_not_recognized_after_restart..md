---
title: "Nvidia Driver not recognized after restart."
date: 2008-03-02
forum: General Help
---

### Post by emunch on 2008-03-02
Hi All,

I've recently installed Gusty to my box which has an Asus M2N-MX MB which has an NVDIA 6100 integrated on. Everything went smoothly till I tried to enable those fancy desktop effects. To sum up; after installing the drivers everything works great but a restart ruins everything. After i restart the computer it states that I need to configure my resolution because it's not configured! I don't know what I'm doing wrong.

Some more info:
- AMD 64, using the "NVIDIA-Linux-x86_64-169.12-pkg2"
- stopped the gdm and "$ sudo sh NVIDIA-Linux-x86_64-169.12-pkg2"
- started the gdm and saw nvidia screen and system resolution is the way it's supposed to be 
- restarting the system. 800*600 no configuration no selection enabled.

Thanks to all in advance.

Cheers.

---

### Post by brabo on 2008-03-02
hi,

so, you configure and it works, but after a reboot you're thrown in at 800*600,
do i get this right?
something that may help, is some fiddling in xorg.conf.
it helps when using "nv" driver, so it may also do the trick for you.
first, to be sure you can rectify possible problems, do a "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.good"
if the following doesn't work, or messes it up completely, you can login in a shell and turn back the changes. Then:

gksu gedit /etc/X11/xorg.conf

look for:

Section "Monitor"
	Identifier	"CB773F-NJ"
	HorizSync	30.0 - 69.9
	VertRefresh	48.0 - 100.0
	Option		"DPMS"

do you have the horizsync and vertrefresh specified? if not, specify them according to your monitor specs.
then, beneath that section you have something like this :

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"CB773F-NJ"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" 
	EndSubSection

make sure that *only* the resolution you want is specified.
like, in my case, i want it to be 1280*1024
it,s possible that there are other lines like this with different depths, modify all of them.
i hope this helps you ;)

brabo.

---

### Post by emunch on 2008-03-03
brabo, 

Thanks a lot for the recommendation. I had it resolved. For some reason I had the xorg.conf file with the failsafe settings and couldn't get it to work by manipulating the file so I decided to reinstall the system and install the drivers again to get a working xorg.conf file. When I finish the installation this time I didn't install it manually, instead I enabled the restricted drivers and let ubuntu do the installation =).  Now it's running just fine! I should have done this in the first place. Honestly I didn't think it would be this easy. =P

Cheers,

---

### Post by willj3440 on 2008-06-13
ok , I am new at ubuntu sort of . This is what is happening . ok , I hit control + alt + f1 I get like a " dos " screen completely black " whole screen " not windowed . I type sudo /etc/init.d/gdm stop then enter password , press enter and gdm stops. then I type sudo sh NVIDIA-Linux-x86-169.12-pkg1.run and the install starts the install say no matching kernal found and gives choice to build a kernal , so I say ok . the build completes . so according to the install everything is fine . so I type sudo /etc/init.d/gdm start , gdm starts back . a box appears saying low resolution 800x600 and shows a generic nvidia driver 6800 , the resolution will not go above 800x600 . then I do a complete restart , thinking that it is just not got everything loaded right . but during boot I get the same low resolution box , I try the nvidia xorg control panel but it say no nvidia driver found . so the control panel tell me to run nvidia-xserver from root . And I do . but still no change in gdm . What am I not doing " or doing wrong ? Also the install disables the restricted nvidia driver .

---

### Post by willj3440 on 2008-06-13
> **emunch said:**
> brabo, 

Thanks a lot for the recommendation. I had it resolved. For some reason I had the xorg.conf file with the failsafe settings and couldn't get it to work by manipulating the file so I decided to reinstall the system and install the drivers again to get a working xorg.conf file. When I finish the installation this time I didn't install it manually, instead I enabled the restricted drivers and let ubuntu do the installation =).  Now it's running just fine! I should have done this in the first place. Honestly I didn't think it would be this easy. =P

Cheers, but does the restricted drive allow u to run 3d cube and all the effects . my orginal problem was in 3d cube it only show 2 windows and would not allow for cube to zoom in and out . thats was why I was doing a manual install .

---

