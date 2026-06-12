---
title: "Ubuntu can't start X"
date: 2005-10-19
forum: General Help
---

### Post by commodore on 2005-10-19
Just before the log in screen should appear, ubuntu says it can't start x window manager. Ubuntu then wants to open a file where I could get information but the window kind of thingie is wierd and enter nor arrow keys don't work. What's wrong? The last command i run was the first one in multimedia codecs at ubuntuguide.org. The site was down when i posted this so I couldn't check what it was.

I'm starting to think that windows IS better than linux because i have had sooo many more errors on ubuntu than on windows. And now it doesn't even start!

---

### Post by KingBahamut on 2005-10-19
Xserver failure. What is your hardware configuration? Video card make and model? Monitor?

---

### Post by commodore on 2005-10-19
I want to say that it worked before.

My monitor is something by fujitsu siemens. My graphics gard is NVIDIA GeForce 6600.

---

### Post by commodore on 2005-10-20
Noone can help me?

---

### Post by rjwood on 2005-10-20
[quote=commodore]Noone can help me?[/quote]
I am sure it will get worked out--but be patient. when you get into the info screen the keys that you can use are the tab and enter keys.

Did you install nividia drivers? Either from syanptic or nvidia web site?

---

### Post by commodore on 2005-10-20
No I didn't. There was no information about it.

---

### Post by KingBahamut on 2005-10-20
At a command line 

apt-get install nvidia-glx 
sudo nvidia-glx-config enable 

then reboot to correct.

---

### Post by commodore on 2005-10-21
How do I get to the command line? I don't know how to do that without gnome.

---

### Post by rjwood on 2005-10-21
[quote=commodore]How do I get to the command line? I don't know how to do that without gnome.[/quote]
where are you now---what do you see?

---

### Post by Predius on 2005-10-21
You can try starting on Single user mode, which is the second one when you choose your OS.

---

### Post by commodore on 2005-10-23
I managed to install the nvidia drivers. Almost nothing changed. I wrote down the error message: "I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"
The keyboard absolutely frozes then. Not even numlock works.

---

### Post by bl4ckm0r3 on 2005-10-23
Actually I'm having the same problem...i've a philips 107p and a geforce 4 mx 200 and i've installed the nvidia drivers with apt!
Two days ago it freezed during the gdm boot and now i can't use nvidia drivers.
I've to switch into single user mode and change my xorg.conf video-card-driver-entry with nv and it starts without problems.
There's a question, where can i find what error is it?Is there an error.log somewhere?

ps I've tried to reconfigure the nvidia-glx package with dpkg-reconfigure, then i started gdm and it worked, but when i rebooted gdm was freezed again!

---

### Post by moglenstar on 2005-10-23
did you upgrade to breezy from hoary/warty?

if so you might need to edit your xorg.conf

from the console type:

sudo nano /etc/X11/xorg.conf

look for the section called "InputDevice"

if it has 

'Driver        "keyboard" '

change it to

'Driver        "kbd" '

then ctrl+x to exit, press y to save, and then try to startx

---

### Post by bl4ckm0r3 on 2005-10-23
it is already kbd!and i upgraded to breezy when the rc was out!i've never had this problem since now!

---

### Post by moglenstar on 2005-10-23
[QUOTE=bl4ckm0r3]it is already kbd!and i upgraded to breezy when the rc was out!i've never had this problem since now![/QUOTE]


my reply was aimed at the creator of this thread :)

your problem sounds like something different

---

### Post by rjwood on 2005-10-23
both of you should try 

sudo nividia-glx-config enable

then

sudo dpkg-reconfigure xserver-xorg

commodore if that doesnt work do
sudo nano /etc/X11/xorg.conf

when the file pops up find the "device" section and change the driver from "nvidia" to "vesa". 

Let me know what happens.
keep staying with it-we will get it fixed;)

---

### Post by commodore on 2005-10-23
No it still doesn't work. Linux just doesn't work then. I'll start using windows?

---

### Post by rjwood on 2005-10-23
[quote=commodore]No it still doesn't work. Linux just doesn't work then. I'll start using windows?[/quote]

can you post your xorg.conf file so I can look at it?

---

### Post by commodore on 2005-10-24
I don't know how to copy the file from ubuntu to windows. I wrote something down but I got tired so it's not much. I can't reinstall ubuntu because I have files on it that I still need.

Section "Module"
"Gleore"
"bitmap"
"ddc"
"dri"
"extmod"
"freetype"
"glx"
"int10"
"type1"
"vbe"

Section "Input Device"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"

Section "Input Device"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"

Section "Device"
Identifier "NVIDIA Corporation NV43 [GeForce 6600]"
Driver "vesa"
Bus ID "PCI :1:0:0"

Section "Monitor"
Identifier "C700"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-160


There's probably a lot of mistakes.

---

### Post by rjwood on 2005-10-24
Do you see the link on my signature that ends with nvidia?
Click on that - go to that thread and ask tseliot for help, he is very knowledgeable with this and can probable solve your problem. You might want to read the thread while you wait.

Don't get discouraged as I have found out that there is nothing that can not be fixed. You are getting an education thru this and it will be very valuable. Take my word for it..

---

### Post by lardiop on 2005-10-24
Exact same problem, 5.10 Live with a Radeon X800XL

---

### Post by commodore on 2005-10-25
Heh welcome to the club lardiop. Yeah, I know it's an old joke but I haven't had an opportunity to use it.

Can't i just reinstall x?

---

### Post by jpilloni on 2005-10-25
I have the same problem, but when I try the suggested solution

"[I]sudo nvidia-glx-config enable

then

sudo dpkg-reconfigure xserver-xorg

commodore if that doesnt work do
sudo nano /etc/X11/xorg.conf[/I]"

I get errors for the first two options. In the first one, it tells me that the xserver package is not installed or not installed correctly.

The second line tells me that xserver-org is broken or not fully installed.

If I try the last one, it opens an empty file.

I have the installation CD, but I have no idea on how to install the pakage from there. Any ideas? 

Thank you.

---

### Post by tseliot on 2005-10-25
[QUOTE=commodore]Can't i just reinstall x?[/QUOTE]

Try this:

sudo apt-get install --reinstall xserver-xorg

---

### Post by sanjose on 2005-10-25
[quote=commodore]I don't know how to copy the file from ubuntu to windows. I wrote something down but I got tired so it's not much. I can't reinstall ubuntu because I have files on it that I still need.[/quote]

if you can boot from windows you can copy your:
[INDENT]**/etc/X11/xorg.conf **and
  **/var/log/Xorg.0.log**
[/INDENT] and paste it here.



you can access your linux partition from windows using this:
[INDENT]**[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)**
[/INDENT]

---

### Post by commodore on 2005-10-25
Sanjose thank ya, it's a useful app.

Here's my xorg.conf:
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"ee"
	Option		"XkbVariant"	"pc105"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	Driver		"nvidia"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"C700"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"vesa"
	Monitor		"C700"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by tseliot on 2005-10-25
Commodore, please try to reinstall the xserver as I had suggested above.

---

### Post by commodore on 2005-10-26
Ok, I'll try. But I'm a bit afraid. My friend sayd it's not easy.

---

### Post by commodore on 2005-10-26
I got this error while reinstalling x:
xserver-xorg postinst warning: not updating /etc/X11/xorg.conf; file has been customized.

I started downloading breezy iso, i'm reinstalling ubuntu. Maybe I should install a different disto?

---

### Post by tseliot on 2005-10-26
[QUOTE=commodore]I got this error while reinstalling x:
xserver-xorg postinst warning: not updating /etc/X11/xorg.conf; file has been customized.

I started downloading breezy iso, i'm reinstalling ubuntu. Maybe I should install a different disto?[/QUOTE]

You should try the livecd first so as to see if everything works ok with your hardware. You should try Breezy's livecd but you might also try PCLinuxOS or Knoppix or Suse livecd.

Of course you should try Breezy's first

---

### Post by sanjose on 2005-10-26
[B]commodore

[/B]how about /var/log/Xorg.0.log or Xorg.20.log

---

### Post by commodore on 2005-10-26
The o.log file:

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ville 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 26 11:52:32 2005
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined Device "vesa" referenced by Screen "Default Screen".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by RAOF on 2005-10-26
Edit: Or even better, just take the advice below.  He knows more than me :)

---

### Post by sanjose on 2005-10-26
under

[B]Section "Screen"
[/B] [INDENT]   [INDENT][B]Device "vesa"
    [/B]
try changing ***"vesa"*** to 
    ***"NVIDIA Corporation NV43 [GeForce 6600]"***
  [/INDENT] [/INDENT] 
then reboot see if that will work

---

### Post by commodore on 2005-10-26
It was NVIDIA Corporation NV43 [GeForce 6600] before, but someone said I should change it to vesa. I allready changed it back to NVIDIA Corporation NV43 [GeForce 6600] a long time ago.

---

### Post by sanjose on 2005-10-26
[quote=commodore]It was NVIDIA Corporation NV43 [GeForce 6600] before, but someone said I should change it to vesa. I allready changed it back to NVIDIA Corporation NV43 [GeForce 6600] a long time ago.[/quote]


did it work when you change ***vesa*** to ***NVIDIA Corporation NV43 [GeForce 6600]***

---

### Post by CrayMk7 on 2005-10-26
I had the the same problem after a clean install, over and over again x would refuse to work, I narrowed it down to my new add on sata raid card. If i
I use my four sata disk in software raid everything is fine, if I use them trough my raid card also with software raid, x will refuse to work. I triple checked it and its the same basic xorg.conf file being created every time, but with the card it won't work without it it will...

This was with the pre release...

---

### Post by commodore on 2005-10-27
I reinstalled ubuntu. The wierd thing is that my upgraded breezy looked totally different from a clean install. Does this mean I have to make a clean install every time a new release comes out? I'm starting to think ubuntu isn't as good as people are saying, but I think it was my fault this time.

---

### Post by rjwood on 2005-10-27
[quote=commodore]I reinstalled ubuntu. The wierd thing is that my upgraded breezy looked totally different from a clean install. Does this mean I have to make a clean install every time a new release comes out? I'm starting to think ubuntu isn't as good as people are saying, but I think it was my fault this time.[/quote] 
I am happy it is working for you now. You stuck with it---good for you. 
that show determination. 

I have had to install/reinstall probably 5 times. Only because I didn't know enough.
But It taught me alot about this system and I still have alot to learn.

I think Ubuntu is great. Even though it requires me to understand more of the inner workings of the operating system I am willing to learn. That is better than spending all my time having to shop around for the lastest and most effective anti-virus and anti-spyware and constantly playing defense with ms windows.

Congradulations commadore and good luck!!!:KS

EDIT: Thanks to all the wonderful people who did their best to help.
This is a great community forum

---

### Post by commodore on 2005-10-27
rjwood, I don't have spyware nor antivirus protection installed :D

---

### Post by rjwood on 2005-10-27
[quote=commodore]rjwood, I don't have spyware nor antivirus protection installed :D[/quote]

Me either---that's my point.

although it is probably a good idea to safeguard yourself with what ubuntu offers for protection.. I am behind a router so I feel safe with that firewall. Clamav is a decent antivirus software and stays up to date.

---

### Post by Nerdo on 2007-12-18
I'm getting this problem on NVIDIA Geforce Ti 4200

I get the error

Undefined Device "(null)" referenced by screen "Generic Monitor"

Fatal Server Error
no screens found

I only have 2 line in the xorg.conf about the device [Screen] but thats all that dpkg-reconfigure puts in their no matter how many times I run it, I tried reinstalling X but it says dependent xserver-xorg-core

And then quits with the error
E: Broken Packages

Please Help!

---

