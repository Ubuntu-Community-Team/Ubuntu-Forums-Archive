---
title: "Beryl and xfce4"
date: 2006-11-29
forum: General Help
---

### Post by yosef on 2006-11-29
Can beeryl work with xfce4?  I like xubuntu (the clean and speedy xfce desktop) and beryl eyecandy is great, can I have them together? When I try it doesn't work.

---

### Post by fuscia on 2006-11-29
i just tried, myself, and couldn't get it to work. i got some kind of gtk icon error.

---

### Post by john.nicholls on 2006-11-30
I have Beryl and xfce working together, sort of. I'm still experimenting.
What error messages and problems do you see?

John

---

### Post by forcesofhabit on 2006-11-30
I'm using Beryl and XFCE4 but I'm not getting any Eye candy or effects...
The icon is in the tray... anything I should know about specifically using this?

---

### Post by yosef on 2006-12-01
First off, I want to thank you guys for helping me out.  Beryl works just fine in both kde and gnome on my computer, its just the xfce4 desktop thats giving me trouble here.

These are the messages I get:

yosef@rlyeh ~> beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :0.0


yosef@rlyeh ~> beryl-manager
yosef@rlyeh ~> libGL warning: 3D driver claims to not support visual 0x5b
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :0.0

this actually leaves the beryl icon in the system tray, so I guess beryl is running, but its not doing anything.

yosef@rlyeh ~> emerald
emerald: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.

when I enter the "emerald --replace" option I get get nothing, the terminal just hangs there, not giving me a prompt just waiting.

yosef@rlyeh ~> emerald-theme-manager

this pops up a window giving me choices of themes which then do not effect anything.

---

### Post by yosef on 2006-12-05
Bump!

---

### Post by el_itur on 2006-12-07
Can we just punish the users that post message like bump!, munf!, crap!, and so on.

If you don't hace a question/answer just don't post, beans don't worth it

---

### Post by Sunnz on 2006-12-10
No I like to see someone post the solution too since I am having the same problem here.

---

### Post by yosef on 2006-12-12
nobody has any helpful advice?

---

### Post by john.nicholls on 2006-12-12
Accprding to another writer on this forum,the problem is that xfwm4 conflicts with beryl and keeps it from running properly. He suggests you should remove xfwm or issue the command kill xfwm.

---

### Post by jozmak on 2006-12-16
I've just installed beryl on xubuntu edgy and it works perfectly for me. I am using nvidia card and these are the steps, I followed. 
 
Install beryl by following the instructions on the beryl website:

[http://wiki.beryl-project.org/wiki/Install/Ubuntu](http://wiki.beryl-project.org/wiki/Install/Ubuntu)

But don't follow their nvidia driver installation procedure. Rather use the one in "Step 2" below.
 
1) Download the newest nvidia driver from the nvidia website (9631).
2) Install the driver by following exactly "installation METHOD 2" (!!!) on this site:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

When the installation is complete, don't forget!!! modifying the 

/etc/default/linux-restricted-modules-common file by entering the following line:
DISABLED_MODULES="nv"

The xorg.conf file should include the following lines (options):

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video CardNVIDIA GeForce MX 440"
	Monitor		"Generic Monitor"
	Option         "AddARGBGLXVisuals" "True"
             Option         "DisableGLXRootClipping" "True"
             Option         "TripleBuffer" "true"
	DefaultDepth	24
........
Also these sections:

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Depending on your video card, it is possible that you don't need the "Extensions" section. If everything looks ok but beryl wont start enable it. 

Run the 

 glxinfo | grep direct 

command to make sure that you have direct rendering. 

4) Reboot xubuntu, open the "Settings>Autostarted Applications"  and add "beryl-manager" to the list. Reboot. If everything went fine you should boot into beryl. It will automatically disable xfwm4.

(Note: After rebooting, you might end up with resolution problems; if this is the case, you should run the  "sudo dpkg-reconfigure xserver-xorg" command. On xubuntu, I had to do this but on ubuntu this was not necessary. Do the reconfiguring and go back to Step 4)
 
Note: If you disable beryl by any reason, you will have to manually restart xfwm4 window manager to get it run. 

Good luck

Jmak

---

### Post by wgscott on 2006-12-21
The website is apparently down at the moment, but I did this yesterday and followed the directions on this page:

[http://xubuntuguide.org/tiki-index.php#Installing_Beryl_Xgl_with_Nvidia_cards](http://xubuntuguide.org/tiki-index.php#Installing_Beryl_Xgl_with_Nvidia_cards)

---

### Post by yosef on 2006-12-24
Can this be done with ati as well? ANyone know of a howto for that?

---

