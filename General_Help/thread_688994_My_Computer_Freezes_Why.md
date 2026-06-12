---
title: "My Computer Freezes Why?"
date: 2008-02-05
forum: General Help
---

### Post by adn258 on 2008-02-05
Okay my laptop at times just freezes but yet everything is running like the cpu I know this because last time and had system monitor up when it happend but then when it happens you can click anything and not even control alt delete brings up anything it just won't do anything and you have to do a hard shutdown.  This has been happening and like IDK but I think it might only be happening like when I have a lot of stuff going on in my workspaces ESPECIALLY THE TOTEM player.  I think what should I do?

---

### Post by Rome.konig on 2008-02-06
did you set a large enough swap space when you installed Ubuntu? or sometimes its just a bug.

---

### Post by adn258 on 2008-02-06
> **Rome.konig said:**
> did you set a large enough swap space when you installed Ubuntu? or sometimes its just a bug.

I got way more ram than I need 2 gigs so it doen't even come close I think it's a bug but if it happens what can I do?  Is there anything else I an do besides do a hard shutdown i.e. turn computer off with button?  Also I think it was related to the BURN EFFECT when applications closed casue that's all I had for closing applications and or the totem player which kinda has problems in fact due to my graphics card the totem player doesn't like to work unless it's set right my graphics card was blacklisted.  Any ideas people?

---

### Post by hyperair on 2008-02-06
What is your graphics card?

---

### Post by adn258 on 2008-02-06
> **hyperair said:**
> What is your graphics card?



here's all my stuff below just in case also I set totem player so it would play because earlier becasue I changed one of the settings

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
austin@Bomb:~$

---

### Post by hyperair on 2008-02-06
Intel graphic card eh? Shouldn't be blacklisted IMO. Please post your /etc/X11/xorg.conf as well.

---

### Post by tgalati4 on 2008-02-06
If you dual-boot with Windows, then there is an issue with having an NTFS mount active.  It sometimes causes a temporary freeze.  If you have that mount in your /etc/fstab, try commenting it out and see if the behavior changes.

---

### Post by adn258 on 2008-02-06
> **hyperair said:**
> Intel graphic card eh? Shouldn't be blacklisted IMO. Please post your /etc/X11/xorg.conf as well.

below is that :).  :/ I don't know what to say it's happened twice lately along with this error below when I start uip the computer once I restart it's okay on that one though.  When it freezes though it's really weird it's almost like things still work music stills plays if it's playing but that's it you can't do anything you can't click on anything or nothing things move even it's so odd but your stuck you can't do anything.   

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

___________




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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"

---

### Post by hyperair on 2008-02-06
Oh in that case, it's probably becaues Compiz Fusion hung. It does that sometimes. You should report a bug at launchpad, providing the details as you have done here. For the meantime you should try seeing what can consistently reproduce the error as bugs such as this become easier to fix if you can reproduce the error consistently.

---

### Post by adn258 on 2008-02-06
> **hyperair said:**
> Oh in that case, it's probably becaues Compiz Fusion hung. It does that sometimes. You should report a bug at launchpad, providing the details as you have done here. For the meantime you should try seeing what can consistently reproduce the error as bugs such as this become easier to fix if you can reproduce the error consistently.

Your right friend I think it has something to do with the burn effect but I am not sure 100%.

---

### Post by hyperair on 2008-02-07
=\ Why don't you keep experimenting with it until it hangs again? Either way you don't need to hard reboot. Since you've noted that everything else's working (e.g. sound), all you need to do is switch to one of your ttys (Ctrl+Alt+F[1-6]).  But it won't work at first because X has grabbed your keyboard. So what you do is Alt+SysRq+R, then Ctrl+Alt+F1. Log in, then run this command: "killall -9 compiz.real". Then switch back to your GUI (Ctrl+Alt+F7). Things should work, but without effects. You can turn it back on after that.

---

### Post by adn258 on 2008-02-08
> **hyperair said:**
> =\ Why don't you keep experimenting with it until it hangs again? Either way you don't need to hard reboot. Since you've noted that everything else's working (e.g. sound), all you need to do is switch to one of your ttys (Ctrl+Alt+F[1-6]).  But it won't work at first because X has grabbed your keyboard. So what you do is Alt+SysRq+R, then Ctrl+Alt+F1. Log in, then run this command: "killall -9 compiz.real". Then switch back to your GUI (Ctrl+Alt+F7). Things should work, but without effects. You can turn it back on after that.

alright thanks a lot dude

---

### Post by hyperair on 2008-02-09
No problem.

---

### Post by MarkkuK on 2008-03-28
I also have Ubuntu 7.10 completely freezing. the problem is now pretty easily reproducible by starting a file transfer using SCP. Freezing does not happen when when I use WLAN - only with Ethernet. So this would suggest that there is a bug either in the Ethernet driver or controller. Interestingly my notebook (FSC Amilo Pi2550)  has the same RTL8101E PCI Express Fast Ethernet controller an the OP. Has anyone else observed similar behavior and/or has perhaps found a solution?

---

