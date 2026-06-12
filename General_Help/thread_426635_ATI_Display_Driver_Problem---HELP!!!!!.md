---
title: "ATI Display Driver Problem---HELP!!!!!"
date: 2007-04-28
forum: General Help
---

### Post by gordo1701e on 2007-04-28
Greetings to all!!!

As I'm relatively new to this forum and linux in general, please forgive me if this is posted in the wrong spot.  Anywho,  Here goes..  I;ve got a huge problem with the Proprietary ATI driver when running Ubuntu or any other Linux distro I've tried.  This also includes Kubuntu and SUSELinux.

It doens't seem to matter what I do, as soon as I INstall the driver and reboot all I get is the BLack Screen of Death (7.04) or the Ubuntu logo with the progress frozen beneth it(6.10).  I've read the Instalation guide for Both Versions and Edited my Xorg.conf file to the point where it can sometime become unrecognizable.  the dumb thing is the same said ATI card, works flawlessly under Windows XP MCE 2005 and Vist X86 and X64 Variants.  What Gives???   BTW, I've tried installing with both VGA and DVI on my monitor.

Hardware Specs:
Kernel Version: Irrelevant, Happens with all versions
Driver: Anything from ATI or Ubuntu, FGLRX related.
Mainboard: Foxconn/FIC C51GU01(from Gateway)
Chipset:Nvidia NForce 4.
GPU: ATI Radeon X1300 Pro PCI-Express X16 256Mb
CPU: AMD Athlon 3800+ 64X2 Dual Core Socket 939
Mainboard BIOS ver:6.00 Feb 2006(most recent Avail.)
Monitor: DTECH 9151 Dual Mode 19" monitor  Max Res 1280x1024 @ 75Hz DVI  1900x1280 @ 60Hz VGA PNP monitor


Any ideas would be appreciated as I've already googled this for over year and am about ready to pack it in a go to Vista.:( 

Regards/

---

### Post by conehead77 on 2007-04-28
I had similar problems with my ATI X700. Maybe this link will help you: [http://ubuntuforums.org/showthread.php?t=399913&highlight=beryl+ati+feisty]("http://ubuntuforums.org/showthread.php?t=399913&highlight=beryl+ati+feisty")

Scroll to the "VIDEO" section and follow the instructions.

I also played around with the "sudo dpkg-reconfigure xserver-xorg" (not sure if its the exact command)

---

### Post by gordo1701e on 2007-05-09
Much thanks for the info!!!  I'd almost given up hope here!!!

Ok, this is really starting to Tic me off!!!!  no matter what I do or try this Damn ATI Card just WON'T work with Linux!!!!:(  I don't know what else to do.  I've tried just about every piece of advice I can get my Hands on and nothing!!!  Every time I try to reboot, all I get is the Black screen of Death.  Is the X1300 Pro PCI-e Card not supported or something???  I give UP!!!!!!  I'd really like to know how others have done it!!!

---

### Post by Nate53085 on 2007-05-13
I am having the same problem with my ATI X1300  AGP card.  If I figure anything out I will let you know.

---

### Post by adarkenigma on 2007-05-14
i had similar problem with ATI x1400  i tried both xorg-fglrx and official release from ATI 8.36.5 

this is wat i did to make it work 

first backup ur xorg.conf (if something goes wrong) 

```
sudo apt-get install xorg-driver-fglrx 
```

then go to xorg.conf 

add 

```
Section "Extensions"
        Option  "Composite" "0" 
EndSection
```  

at the end of xorg.conf

remove 

```
InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
``` 
under  "ServerLayout" section

then i removed 

```
Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection 
```

then run 
```
sudo aticonfig --initial --force 
```

then run 
```
 sudo depmod -ae 
``` 

note that i have added  "e" after which is not shown in official guide 

then 

```
 sudo aticonfig --overlay-type=Xv 
``` 

which will add following to xorg.conf  under device section 

```
    Option       "VideoOverlay" "on"
        Option       "OpenGLOverlay" "off"
```

then add "TexturedVideo" "on" under device section 

```
 Option  "TexturedVideo" "on" 
``` 

also add 
```
Option "AIGLX" "off" 
``` 

under ServerLayout section 

save xorg.conf file and reboot  if you still get black screen then run 
```
 sudo depmod -ae 
```  again 

that did the trick for me .. i tried official drivers too but i really didnt see any difference between xorg and ATI's driver

hope that helps

---

### Post by jocko on 2007-05-14
Often the file /var/log/Xorg.0.log will contain important clues to why xorg fails to start.
Next time you try to start xorg with the fglrx driver and it fails, run this command in a terminal (ctrl-alt-f1):
```
cat /var/log/Xorg.0.log | grep EE
```
Or to save the output as a text file in your home directory (to be able to copy/paste it here):
```
cat /var/log/Xorg.0.log | grep EE > ~/filename 
```
If there are any errors you'll see a line starting with "(EE)" describing each error.
Hopefully someone here will understand the problem.

---

### Post by RedSquirrel on 2007-05-14
[Installing Ubuntu 7.04 (Feisty Fawn) on machine with ATI X**** series video cards]("http://ubuntuforums.org/showthread.php?t=414194")

---

### Post by applefreakpeeps on 2007-06-29
Not fixed with 8.38.6

---

