---
title: "No Virtual Terminals in Gutsy"
date: 2007-10-20
forum: General Help
---

### Post by Ultra Magnus on 2007-10-20
Hi, I just realised that I don't have any virtual terminals (<ctrl><alt>F1-F6) - How do I get them back? Has anyone else had this problem?

---

### Post by Subban on 2007-10-20
> **Ultra Magnus said:**
> Hi, I just realised that I don't have any virtual terminals (<ctrl><alt>F1-F6) - How do I get them back? Has anyone else had this problem?

I have just realised mine are also gone :O

---

### Post by BennBuntu on 2007-10-20
Mine are still there, I did see something about an Nvidia drivers bug related to virtual terminal. I'm running Nvidia and don't have any problems so I didn't read any more, could have something to do with it, new drivers are meant to fix it.

running standard 32 bit gutsy install, compiz effects on, nvidia 6600

edit: this was news, maybe not related [http://www.phoronix.com/scan.php?page=news_item&px=NjEzOA]("http://www.phoronix.com/scan.php?page=news_item&px=NjEzOA")

---

### Post by darylb on 2007-10-20
Hi, mime are gone too after gutsy upgrade. I just noticed when nautilus locked up my entire gnome session and I wanted to kill it from a virtual terminal. I'm running a laptop with no nvidia card though, so my problem at least, is not related to the nvidia drivers.

EDIT: found the solution at here:
[http://ubuntuforums.org/showpost.php?p=3419199&postcount=16](http://ubuntuforums.org/showpost.php?p=3419199&postcount=16)
Worked for me!

---

### Post by chrisccoulson on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Have you seen this thread: [http://ubuntuforums.org/showthread.php?t=581071]("http://ubuntuforums.org/showthread.php?t=581071")

---

### Post by dietrying on 2007-10-20
same problem here......
:(:(:(

---

### Post by Subban on 2007-10-20
```
sudo modprobe vga16fb
sudo modprobe fbcon
```

referenced in this thread : [http://ubuntuforums.org/showpost.php...9&postcount=16](http://ubuntuforums.org/showpost.php...9&postcount=16)

I assume that is just entered into a terminal, however the virtual terminals are still gone, or does it require a reboot or something ?

I am wary to reboot without a good reason as my motherboard and bios are dieing, it sometimes won't come back up :[

---

### Post by dietrying on 2007-10-20
[I]assume that is just entered into a terminal, however the virtual terminals are still gone, or does it require a reboot or something ?

I am wary to reboot without a good reason as my motherboard and bios are dieing, it sometimes won't come back up :[
[/I]

hi Subban
this trick didn't work for me too......
using nvidia driver and pressing strg+alt+F** only brings blank screens (out of range)
i reported a bugreport:

[https://bugs.launchpad.net/ubuntu/+bug/155100](https://bugs.launchpad.net/ubuntu/+bug/155100)

if you have the same problem, please confirm.
David

---

### Post by meldroc on 2007-10-23
Just noticed similar behavior.  It's more likely to happen after I suspend and wake my laptop (Nvidia Geforce Go 7700 GPU) - when I press Ctrl-Alt-F1, I find my virtual terminals area all mangled, with flickering horizontal lines.

Can somebody tell me what the hell is wrong with Nvidia?  We have this, suspend/wake hangs (I work around mine by having something OpenGL running, like Compiz, otherwise I hang with a black screen), display glitches, virtual terminal mangling, etc. These have been recurring problems with the drivers that have continued to plague us for literally years now.  The Nvidia proprietary drivers have gone through a dozen revisions, and each and every time, users have complained about these bugs, and THEY STILL ARE NOT FIXED.

I say it's time to form a mob with torches and pitchforks, and converge on Nvidia's offices and demand they fix this crap.

---

### Post by Subban on 2007-10-24
I have been checking daily but not seen a fix for this yet, anyone got one ?

---

### Post by Soarer on 2007-10-24
It is news to me that you could do this! However, I can't as I just get a blank screen & cursor (but ctrl-alt-f7 brings me back to X OK). I am running the new nVidia drivers on Gutsy 64bit.

---

### Post by timmyw29 on 2007-10-24
Almost identical to what Soarer explained, here. I hit Ctrl+Alt+F... and get a black screen with nothing but a cursor, can't type at all or anything. But I can Ctrl+Alt+Backspace to bring X back up, or Ctrl+Alt+F7 or F8 seem to work as well.

I discovered this issue while trying to do the readahead tutorial - found [here]("http://ubuntuforums.org/showthread.php?t=565651").

Hopefully there's some resolution to this problem.

---

### Post by Subban on 2007-10-25
Really still no fix for this ?

---

### Post by frodon on 2007-10-27
The fix worked for me, thanks for sharing this you saved me many times.

---

### Post by fwhr on 2007-10-27
My Ctrl+Alt+F did'nt worked, too
So, I opened a terminal and typed
```

sudo modprobe vga16fb
sudo modprobe fbcon
```
Checking... After that commands I can use Ctrl+Alt+Fx to open a virtual terminals again...
I just added this lines :
```

vga16fb
fbcon
```
into /etc/modules
and Ctrl+Alt+Fx works for me after reboots, too.

---

### Post by Subban on 2007-10-27
I tried doing :
```
sudo modprobe vga16fb
sudo modprobe fbcon
```

Ctrl+Alt+Fx still is blank, could it be a problem in my xorg.conf ?
I wondered if it is because only 24bit depth seems to be defined and perhaps the terminals are 16bit ?

```

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
	Option		"XkbLayout"	"gb"
EndSection

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mice"
#	Option		"Protocol"	"ImPS/2"
#	Option		"ZAxisMapping"	"4 5"
#	Option         "Buttons"	     "7"
#EndSection

Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB RECEIVER"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"nvidia"
	Busid		"PCI:5:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Xerox XA7-19"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GS]"
	Monitor		"Xerox XA7-19"
	Defaultdepth	24
	SubSection "Display"
Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	InputDevice     "Logitech MX1000" "CorePointer"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection
```

---

### Post by jordoex on 2007-10-27
Hi, i had the same problem as soarer and timmyw29 and the modprobe fix works.  I'm using a nvidia 8600 on a laptop, if that helps anything.

---

### Post by Subban on 2007-10-28
> **jordoex said:**
> Hi, i had the same problem as soarer and timmyw29 and the modprobe fix works.  I'm using a nvidia 8600 on a laptop, if that helps anything.

I am using a nvidia 7600 (exact model I am afraid I can't remember, xorg.conf says a GS)

I have tried defining the exact screen rates for the monitor in xorg.conf, as show below.

```
#Section "Monitor"
#	Identifier	"Xerox XA7-19"
#	Option		"DPMS"
#EndSection

Section "Monitor"
    Identifier     "Xerox XA7-19"
    HorizSync       30.0 - 64.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection
```

It has done nothing to help after restarting X (ctrl+alt+backspace)

I really am at a loss as to what to do next.

---

### Post by fwhr on 2007-10-28
Subban, try this:
in the **/boot/grub/menu.lst** delete **splash** and **vga=xxx** from kernel line, 
or press "**e**" key before booting to edit this line and then press "**b**" to boot to check will it works.

---

### Post by Subban on 2007-10-29
Thank you for the reply Fwhr.

I had previously checked for the vga= option and it was never in my menu.lst, I did try removing the 'splash' option and rebooting, I still have no virtual terminals on ctrl+alt+Fx

Anything else I can try ?

---

### Post by nowshining on 2007-10-29
fx5200 here and used dpkg and chose the nvidia card - no probs here :) and yes it uses the nvidia drivers from nvidia.

---

### Post by stomponthis on 2007-10-29
> **Subban said:**
> ```
sudo modprobe vga16fb
sudo modprobe fbcon
```

referenced in this thread : [http://ubuntuforums.org/showpost.php...9&postcount=16](http://ubuntuforums.org/showpost.php...9&postcount=16)


Thanks that worked first time for me, didn't even need a reboot?

---

### Post by rfurman24 on 2007-10-29
I have no working virtual terminals either. When I alt ctrl f# I get the screen but can not type and can not get back to X. I had to do several hard shutdowns and everything finally started working after fsck. I am affraid to even try the suggestion as I could not get back into Gutsy for sometime last time.

---

### Post by Subban on 2007-11-01
Shamelss bump as I still have had no solution.

To summarize, there was no vga= line in my menu.lst, I have tried removing the slpash from the menu.lst as suggested. I have tried the sudo modprobe lines. 

My xorg.conf is posted earlier in the thread in case its helpful.

---

### Post by jordoex on 2007-11-02
I forgot to add a reminder that if the modprobe solution works, you need to add vga16fb and fbcon to /etc/modules so it still works after restarts.

---

### Post by ebash on 2007-11-02
Edit the file menu.lst and remove the argument "quiet". It worked for me.

---

### Post by Subban on 2007-11-02
> **ebash said:**
> Edit the file menu.lst and remove the argument "quiet". It worked for me.

Thank you for the suggestion.

Tried this now so that I have both 'splash' (someone mentioned it earlier) and 'quiet' removed from the menu.lst and its still not giving me back the virtual terminals /sigh

I do hope this is being worked on upstream (or whatever its refered to) as its a real pain in the bottom sometimes not having these working.

---

### Post by snap on 2007-11-03
Well,  found out the blank virtual terminals were caused in part by the new intel driver :confused:, switched over to i810 driver in xorg.conf and all is fine for me.

I also did the 

sudo modprobe vga16fb
sudo modprobe fbcon

not sure if this is needed,

---

### Post by tech0007 on 2007-11-05
sudo modprobe vga16fb
sudo modprobe fbcon

works for me too!  thanks guyz!

---

### Post by SadaraX on 2007-11-08
1st, thanks for the solution about removing the words 'vga=' and 'splash' from my /boot/grub/menu.lst. This fix worked for me, though my text is big (oh well, can't fix it, and it works okay).

2nd, Subban, I don't know if you already told us, but what nvidia driver are you using? Are you using the restricted driver provided by Ubuntu (what a cool feature!). Or are you compiling your own drivers?

---

### Post by Subban on 2007-11-08
> **SadaraX said:**
> 2nd, Subban, I don't know if you already told us, but what nvidia driver are you using? Are you using the restricted driver provided by Ubuntu (what a cool feature!). Or are you compiling your own drivers?

I am using the restricted driver and nothing exotic/compiled myself.

---

### Post by SadaraX on 2007-11-08
I am not sure what to say. I used to compile my own drivers from the Nvidia provided drivers. Have you tried this?

It is not exactly an optimum situation, but it might help

---

### Post by Subban on 2007-11-08
SadaraX,

No I haven't tried that, I've really been holding out for either a simpler solution that won't break X every time I update the kernal or an update to the driver or whatever is causing the problem initially. If it carries on I may well have to try that so ty for the tip.

---

### Post by thetimekeeper on 2007-11-27
> **fwhr said:**
> My Ctrl+Alt+F did'nt worked, too
So, I opened a terminal and typed
```

sudo modprobe vga16fb
sudo modprobe fbcon
```
Checking... After that commands I can use Ctrl+Alt+Fx to open a virtual terminals again...
I just added this lines :
```

vga16fb
fbcon
```
into /etc/modules
and Ctrl+Alt+Fx works for me after reboots, too.
Worked great for me. Didn't even need to reboot, thank you!

---

### Post by bkraptor on 2007-11-29
Even though it worked for me, I now see a distorted shutdown screen, where everything is a dark shade of grey/black instead of orange. Everything else works.

---

### Post by frodon on 2007-11-29
Yes i have the same thing at shutdown using this fix but that's not important for me so i chose to not fix this :).

---

### Post by broadcast23 on 2007-12-16
sudo modprobe vga16fb
sudo modprobe fbcon

hmm didn't work for me...I have an intel i815 machine here and I think what is happening is that the resolution changes when you try to open a virtual terminal.  I have an old monitor here and when the resoltuon changes on it clicks like there is some relays inside it.  I think that is why I get "logged out of x when I try to open a virtual terminal.  :(

---

### Post by kurazu2 on 2007-12-16
I've got intel 965 mobile graphics card (intel driver). After upgrading from Feisty to Gusty I have no virtual terminals (blank screen). Loading mentioned modules or disabling vga options in grub/menu.lst didn't help. Virtual terminals are gone also in rescue mode. When my system fails, there is no way for me to rescue it without some Live CD.

---

### Post by broadcast23 on 2007-12-16
I can get a terminal when I press ctrl+alt+f1 and to quit press ctrl+alt f7, but when you go to open the terminal in x it just logs me out of x and returns to the login screen.:confused:

---

### Post by broadcast23 on 2007-12-18
You need to check the specifications of your graphics card.  If it is only 16 bit you need to check the xorg.conf file in /etc/x11/  If it says that the color depth is 24 you need to change it to 16.

---

### Post by tontonjoe on 2008-01-17
Hi all,

I'm just trying a Xubuntu in parallel of my Ubuntu, and never took care to these VT's bug. But now I have use of it, there are really missing...

So, for your information, I have the same bug with the Vesa driver, for my ATI Radeon 9800, and the solution works for me: adding the [FONT="Courier New"]vga16fb[/FONT] & [FONT="Courier New"]fbcon[/FONT] modules make the VT's to reappear. 

Great !

---

### Post by dayhawk4 on 2008-02-17
Have a dell inspiron 530N which had ubuntu gusty installed from Dell.  When this system came from the manufacturer,  the virtual terminals were working.  I have noticed though after reading through this that they have since disappeared.  Believe most likely due to upgrades or possibly the installation of some package ..?..  I do know that they were available when I first received this computer, and that this computer came with Ubuntu 7.10 installed.  I hope this helps track down the issue....

---

### Post by pmorch on 2008-03-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135613](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135613) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I was seeing similar problems with the virtual terminals / tty-s. I did not have a vga= setting in menu.lst nor did the modprobe solutions work for me.

I have an intel card, and there is [a known bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135613") in gutsy about this:

For me, switching to the "vesa" driver made the tty / virtual terminals appear again.

Peter

---

### Post by alexebird on 2008-03-07
I had the same problem where none of the ttys would show up.  I fixed it by installing startupmanager from the repository and unselecting the show splash screen check box.

---

### Post by Wastedyouthfx0 on 2008-03-12
Can anybody help me out?  I upgraded to Hardy recently on my work computer and on my laptop at home.  I had blank screens at startup, and was unable to to switch to the virtual consoles, I only saw blank screens.

I added fbcon and vesafb modules, did an update-initramfs, and added fbcon to the blacklist framebuffer file.  I did this on my work and home computer, and finally was able to access the virtual consoles again.  

However, after the latest upgrade, both computers have broken consoles again.  I have a blinking cursor, and can type commands and the computer responds and the cursor moves, I just can't see any text at all.  I can see everything fine at boot up, its just after the X server loads.  

Do I need to reverse what I did because a fixed update was received, and if so how?  I miss my virtual consoles.

---

### Post by Puun on 2008-03-13
same problem here after a fresh install of Gutsy on my laptop.
I reinstalled it due to some previous experiments. Last installation was ok from the verz beginnig.
Now I got no working virtual terminals. Updated all - still nothing

---

### Post by Nythain on 2008-03-14
so, i just figured i would throw this out there...
i didnt have a problem with "blank" tty's but this fix did allow me to resize my console... before, adding vga=795 without enabling the vesafb resulted in my monitor shutting off... now i have a nice pretty 1280x1024 readable console and tty's... thanks much

---

### Post by pmorch on 2008-04-03
I posted to this thread earlier.

I tried to upgrade to Hardy Heron (after making a full backup), and in Hardy the virtual terminals _do_ work. But [there were so many other issues with Hardy, so I went back to Gutsy again]("http://ubuntuforums.org/showthread.php?t=743946")  by restoring my backup and now they don't work any longer of course.

So maybe I'll just wait for Hardy to become ready in due course and hope that my virtual terminals come back again.

Peter

---

### Post by mr_git on 2008-06-01
I'm having the same problem (under Hardy running the restricted nvidia driver) with totally blank virtual terminals on anything except Ctrl+Alt+F7.

```

$ uname -a
Linux pancake 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux
$ cat /proc/driver/nvidia/version 
NVRM version: NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
GCC version:  gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
$ lspci | grep -i vga
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)

```

the modprobe vga16fb / fbcon fix didn't work for me, nor did taking splash out of my grub boot options.

---

