---
title: "few questions, hoping someone can help"
date: 2012-10-15
forum: General Help
---

### Post by 09FordFX4 on 2012-10-15
alright, so i finally found a linux distro that works properly, to an extent on my laptop. half the newer distros wouldnt even load. 

ive got ubuntu 10,04 install on an HP G6 laptop. intel HD 3000 graphics. 

first question, how would i go about getting the screen resolution to a proper widescreen format. only gives me two options in the display settings. 800x600 and 1024x768,

although its not terrible, its still not ideal. i need 1366x768 for my screen. ive tried several things vie found online, xrandr commands etc. none of which worked. is there some kind of thing i can download and do it in? 

also, my mouse trackpad isnt giving me the scroll feature on the right side of trackpad. have to go grab the scroll bar and drag it. again, its not terrible, but a tad annoying at times. 


and one last question, does the cinnamon desktop enviro work with ubuntu 10.04? i really like cinnamon, and want to run it if possible


thanks

---

### Post by papibe on 2012-10-15
Hi 09FordFX4. Welcome to the forums! ):P

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the link here.

Regards.

---

### Post by 3Miro on 2012-10-15
Intel HD 3000 is Sandy Bridge graphics and when those first came out Intel had messed up the driver. It used to be the case that you needed at least Ubuntu 11.04 to get things working. I don't know if the drivers ever got backported to 10.04. You may not be able to get proper graphics on Intel 3000 with Ubuntu 10.04 (11.10 and newer works great).

Your trackpad may be using double-scroll. Check System Admin or Prefs for "Mouse". You should be able to adjust the double-scroll or side scroll from there.

---

### Post by 09FordFX4 on 2012-10-15
> **papibe said:**
> Hi 09FordFX4. Welcome to the forums! ):P

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the link here.

Regards.

here ya go.
[http://paste.ubuntu.com/1282291/](http://paste.ubuntu.com/1282291/)

> **3Miro said:**
> Intel HD 3000 is Sandy Bridge graphics and when those first came out Intel had messed up the driver. It used to be the case that you needed at least Ubuntu 11.04 to get things working. I don't know if the drivers ever got backported to 10.04. You may not be able to get proper graphics on Intel 3000 with Ubuntu 10.04 (11.10 and newer works great).

Your trackpad may be using double-scroll. Check System Admin or Prefs for "Mouse". You should be able to adjust the double-scroll or side scroll from there.

see, the thing is the newer distros boot to a blank screen. cant do anything to avoid it. ive tried many. ubuntu, mint 13, mint 12. oonly the older ones such as ubuntu 10, mint 9, etc. work. so its a bit frustrating

---

### Post by 09FordFX4 on 2012-10-15
small update, updated everything, thinking maybe it would help. no luck. i downloaded gsynaptics, i think thats what i used before on mint 9. but i cant open it. says "GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

im tempted to try updating to ubuntu 12, just scared it wont work again, and i will have to re-install ubuntu 10 all over again. 

honestly, i can live with not scrolling on the trackpad. but the screen res is really starting to bug me

---

### Post by papibe on 2012-10-15
Thanks.

Somehow the intel driver is load, but then unload and the VESA driver is used:
```
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
...
(II) UnloadModule: "intel"
...
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
```
But your EDID data is readable:
```
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff004ca3514200000000
(II) VESA(0): 	00120103802213780a87f594574f8c27
(II) VESA(0): 	27505400000001010101010101010101
(II) VESA(0): 	010101010101121b567250000c303020
(II) VESA(0): 	250058c2100000190000000f00000000
(II) VESA(0): 	00000000001eb4027400000000fe0053
(II) VESA(0): 	414d53554e470a2020202020000000fe
(II) VESA(0): 	00313536415430352d4830370a200003
```
That correspond to this:
```
parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
	Identifier "SEC:5142"
	VendorName "SEC"
	ModelName "SEC:5142"
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1366x768"	# vfreq 60.031Hz, hfreq 46.824kHz
		DotClock	69.300000
		HTimings	1366 1414 1446 1480
		VTimings	768 770 775 780
		Flags	"-HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
EndSection

```
I would try to add this ppa in order to get access to the newer drivers:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```
Then if that doesn't work either, there's another ppa with bleeding-edge versions:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```
(You would have to restart your machine after every upgrade).

To get into a text mode prompt, press Ctrl+Alt+F1 after a few seconds you boot into a black screen.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by 09FordFX4 on 2012-10-15
ok cool i will try those. 
ican i do it in terminal? or that text line thing instead of botting the OS


also, finally got the monitors preference pane to show 1368x768 but when i select it, this pops up (top right hand)

[IMG]http://i48.tinypic.com/2u6mv69.png[/IMG]

---

### Post by papibe on 2012-10-15
> **09FordFX4 said:**
> can i do it in terminal?
Yes, of course.

The Ctrl+Alt+F1 trick was in case you still were booting into a black screen.

Let us know how it goes.
Regards.

---

### Post by 09FordFX4 on 2012-10-15
no dice. didnt work :(

im starting to think i should just reinstall windows and be done with it

---

