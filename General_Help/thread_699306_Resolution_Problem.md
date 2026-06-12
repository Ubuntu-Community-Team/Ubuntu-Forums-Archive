---
title: "Resolution Problem"
date: 2008-02-17
forum: General Help
---

### Post by fourthofjuly on 2008-02-17
I have Viewsonic 17" widescreen LCD monitor (VA1703wb)... original Intel motherboard with onboard graphics,

I am terribly fed up with my screen resolution. I want a perfect 1440 x 900 resolution on my screen, which I get very occasionally after running sudo dpkg-reconfigure xserver-xorg. Am not sure if the problem lies with my monitor or with my graphics card.

Sometimes I get the required output, but after rebooting it switches back to 1024 x 768 resolution. System uses the "Intel experimental modesetting driver". Do I need to install a separate driver for 82945G/GZ?

Output of lspci command

devang@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

If these 2 points are related & can give a clue? 

1) My Intel chipset 82945G/GZ may not be supported, since I had to edit my alsa-base file to make sound working (there is no sound at all on a freshly installed system - neither in Ubuntu, Fedora, OpenSuSE or Sabayon).

2) I can't get my system to wake up after Suspend, some issue with power which may be related here?

Please help....

Regards,

Devang.

---

### Post by ChristosG on 2008-02-17
hi, I didn't want to open a new thread, so I'm writing my problem here, I had XP and I installed Ubuntu too, and when I restart from Ubuntu, everything is normal, when in Ubuntu and I try to shut down my pc, when the orange bar gets empty, my pc doesn't turn off, it stucks at this point, so I have to restart my pc, boot from XP and shut it down from there. How can I solve this? Thanks in advance :-)

---

### Post by Flyingjester on 2008-02-17
you should have opened a new thread christosG, this is totally unrelated to the OPs question. To the OP: suspend is a known issue with ubuntu, many people have this problem, and i believe they are working on a solution.

---

### Post by fourthofjuly on 2008-02-17
> **Flyingjester said:**
> you should have opened a new thread christosG, this is totally unrelated to the OPs question. To the OP: suspend is a known issue with ubuntu, many people have this problem, and i believe they are working on a solution.
any clue for my resolution problem please?

thanks...

---

### Post by fatherdaly on 2008-02-17
You need to make sure that the restricted drivers are enabled. 

System > Administration > Restricted Drivers Manager.

Then make sure their enabled

Also you may need to edit your xorg.conf file to allow your resolution

---

### Post by sammydee on 2008-02-17
Hold on fatherdaly - he's using an intel card! They don't need restricted drivers!

To the OP:

Please post the contents of your /etc/xorg.conf file here and we'll have a look at what could be causing the problem.

Sam

---

### Post by ChristosG on 2008-02-17
Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories  > General Help > Resolution Problem 

I believe that my question fits in this category, I don't want to prevent fourthofjuly from getting an answer, and I don't want to open a new thread for a question that may be too easy to answer. My question is: "I had XP and I installed Ubuntu too, and when I restart from Ubuntu, everything is normal, when in Ubuntu and I try to shut down my pc, when the orange bar gets empty, my pc doesn't turn off, it stucks at this point, so I have to restart my pc, boot from XP and shut it down from there. How can I solve this?"

---

### Post by Flyingjester on 2008-02-17
why do you fight me on this ChristosG, the reason is, it is not similar to the OP's problem. Just start a new thread, preferably with a subject line that describes your problem, so that other people can help you.

also people are coming into this thread to help him with his particular problems. The people looking in this thread might not have the answer to your problem, however if you start your own thread people that might know how to solve your problem will see it in the subject line and look in at it.

---

### Post by fourthofjuly on 2008-02-18
presently I am using 1024 x 768 resolution, since the 1440 x 900 resolution leaves a 1"-2" vertical dark band on the left side of the screen.

[COLOR="Blue"]**the output of my /etc/X11/xorg.conf file is:**[/COLOR]

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"VA1703wSERIE"
	Option		"DPMS"
	HorizSync	24-70
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"VA1703wSERIE"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

---

### Post by fourthofjuly on 2008-02-19
[B][COLOR="Blue"]would appreciate if someone could resolve my problem please...???

thanks & regards,

devang.[/COLOR][/B]

---

### Post by Flyingjester on 2008-02-19
is there any way to manually adjust the horizontal alignment in your monitors menu?

---

### Post by fourthofjuly on 2008-02-20
yes, have tried that, but cannot adjust to such a large extent (almost 1.5" from left)...

regards,

devang.

---

### Post by fourthofjuly on 2008-02-20
[SIZE="4"]please if someone can look into this problem, 

are there any drivers out there for linux that i need to install?

please help... the screen has really started straining my eyes,..

thanks in advance,

devang.[/SIZE]

---

### Post by fourthofjuly on 2008-02-22
would appreciate if someone can resolve my problem...!!!

regards,

devang.

---

### Post by fourthofjuly on 2008-02-23
[COLOR="Red"]**anyone, please ?**[/COLOR]

---

### Post by fourthofjuly on 2008-02-24
i googled for the solution & found auto915resolution startup script created by Roland-Lopez:


[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

i will mark this thread solved if it works... 

many thanks to Roland...

regards,

devang.

---

### Post by fourthofjuly on 2008-02-25
[B]the auto915 resolution thing has not worked, i guess i will file a bug report...

thanks & regards,

devang.[/B]

---

### Post by Astaroth_PoD on 2008-02-26
I have the same issue with Intel and an Acer 2223W, it displays a wide black band on the right side. It's an issue with the Intel experimental driver, and you can fix it if you can manage to turn up the Hz from 60 to something higher - which, unfortunately, I cant :(

Did you post a bug?

---

### Post by suibhne on 2008-02-26
Can any of the above posters post a screenshot of their problem?



I fixed a laptop recently for a friend through the bios settings but i need to know your make and model of computer (not a Dell 1300 by any chance???)

---

### Post by suibhne on 2008-02-26
ooops - i have your specs, didn't read the previous post properly.....


anyway, send me a screenshot of your machine - i'll compare it with some problems i had and see if i can use the same procedure to fix it

I haven't written it down so i'll need to recreate the problem here and remeber how i fixed it that way

---

### Post by Astaroth_PoD on 2008-02-27
There's not much to screenshot as the computer thinks its displaying in the correct resolution (which it is, just not stretched over the whole monitor). I could take a photo of the monitor but it would only show a monitor with a squashed desktop and a 3" black area on the right side.
My MB is a Intel Q35, and the monitor as mentioned an Acer AL2223W. I have however tried this with a laptop with Intel graphics as well, and had the exact same result there.

---

### Post by fourthofjuly on 2008-02-27
> **suibhne said:**
> ooops - i have your specs, didn't read the previous post properly.....


anyway, send me a screenshot of your machine - i'll compare it with some problems i had and see if i can use the same procedure to fix it

I haven't written it down so i'll need to recreate the problem here and remeber how i fixed it that way

[B][COLOR="Blue"]please see the screenshots of 1440 x 900 and 1280 x 768 resolutions.

awaiting your reply,

thanks & regards,

devang.

[/COLOR][/B]

---

### Post by fourthofjuly on 2008-02-27
> **Astaroth_PoD said:**
> I have the same issue with Intel and an Acer 2223W, it displays a wide black band on the right side. It's an issue with the Intel experimental driver, and you can fix it if you can manage to turn up the Hz from 60 to something higher - which, unfortunately, I cant :(

Did you post a bug?
not yet, but i think i should...

---

### Post by chalewa on 2008-02-27
> **Astaroth_PoD said:**
> There's not much to screenshot as the computer thinks its displaying in the correct resolution (which it is, just not stretched over the whole monitor). I could take a photo of the monitor but it would only show a monitor with a squashed desktop and a 3" black area on the right side.
My MB is a Intel Q35, and the monitor as mentioned an Acer AL2223W. I have however tried this with a laptop with Intel graphics as well, and had the exact same result there.


> **fourthofjuly said:**
> [B][COLOR="Blue"]please see the screenshots of 1440 x 900 and 1280 x 768 resolutions.

awaiting your reply,

thanks & regards,

devang.

[/COLOR][/B]


Those screenshots look fine to me, but im guessing that the reason for this is because of what is stated in the post about. 

if i am missing something, please let me know

also, i assume that you have just tried to run a normal 

sudo dpkg-reconfigure xserver-xorg right?



edit: also, at what point does the squishing occur? is the login screen squished, or just after you login? during boot?

---

### Post by fourthofjuly on 2008-02-28
> **chalewa said:**
> Those screenshots look fine to me, but im guessing that the reason for this is because of what is stated in the post about. 

if i am missing something, please let me know

also, i assume that you have just tried to run a normal 

sudo dpkg-reconfigure xserver-xorg right?



edit: also, at what point does the squishing occur? is the login screen squished, or just after you login? during boot?

yes, i ran dpkg-reconfigure, even tried 915resolution & auto915resolution, but doesn't seem to work. I get the desired resolution very very rarely & after I reboot, it again reverts back to some other resolution?

i m filing a bug report now.

thank you for your support & do let me know if you hunt out a solution please...

regards,

devang.

---

