---
title: "Compiz error - ATI Radeon R250 - could not enable..."
date: 2008-01-11
forum: General Help
---

### Post by tiger.woods on 2008-01-11
Another Compiz error, I've not seen anything that would fix my problem so hopefully someone will have some ideas.

I''m getting the following error when trying to start Compiz.

"Desktop effects could not be enabled"

I'm running Gutsey 7.1 on a Dell Inspiron 8500 and the following is from my xorg.conf.
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

I tried running Compiz from the CL and got the following:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 01) (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 

I also tried installing xserver-xgl and that just killed the desktop with a session that lasted less than 60 seconds..

Thanks for any input you can give.

TW,

---

### Post by tiger.woods on 2008-01-15
Anyone have any ideas?

---

### Post by Therion on 2008-01-15
Have you installed **compizconfig-settings-manager** from the repository?

Also, this disturbs me: > Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity I'm certainly no expert but that sounds like (maybe?) you're running a monitor resolution that you're video card can't handle for 3D effects??

---

### Post by tiger.woods on 2008-01-15
Yes.

I just installed the fglrx driver 'apt-get install xorg-driver-fglrx' but I must admit I'm a bit lost on what I'm trying to accomplish...

fglrxinfo shows Mesa as the OpenGL Renderer I'm under the impression it should be ATI??? :confused:.

Thanks,

---

### Post by Therion on 2008-01-15
Hmmm... again I'm no expert, but I seem to be the only person replying so let me suggest, if you're unsure if your ATI driver is installed, to download and run Envy to GET your ATI driver installed:

[ENVY]("http://albertomilone.com/nvidia_scripts1.html").

Good luck!!!

---

### Post by tiger.woods on 2008-01-15
ENVY bombed as has been my experience with it in the past thanks for the suggestion though

Is anyone using compiz with an ATI Radeon 9000 mobile card?

I'm reading posts of people having successes but I'm getting nowhere. I could use some suggestions and a little help.

Thanks.

---

### Post by 3rdalbum on 2008-01-16
Look under System > Administration > Restricted Drivers Manager and see if the ATI driver is loaded. If it isn't, click the checkbox to download and install it.

Then you'll need to install XGL - sudo apt-get install xserver-xgl

Thankfully these days XGL sets itself up - yay for no more text file hacking!

Then you should be able to enable Compiz.

---

### Post by tiger.woods on 2008-01-16
The driver isn't listed in the Restricted Drivers as an option to install even though I have 'linux-restricted-modules-generic restricted-manager' installed... ?

---

### Post by danwood76 on 2008-01-16
Looking at the driver release notes ([here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_712_linux.html")) your card isnt supported by the ati driver.
But it mayt work as my desktops card isnt listed either and it works perfectly.
That may be why the ATI driver isnt listed in the restricted drivers utility.

Try installing the driver from this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
Envy isnt very good at installing the drivers properly in my opinoin.

regards,
Danny

---

### Post by tiger.woods on 2008-01-16
So am I going after the ATI driver? I'm just a little confused on the link you provided..

Thanks,

---

### Post by danwood76 on 2008-01-16
yeah try and install the ati driver you can get from their site.
the chances are that your card isnt supported as its quite old though.

regards,
Danny

---

### Post by ugm6hr on 2008-01-16
> **tiger.woods said:**
> ENVY bombed as has been my experience with it in the past thanks for the suggestion though

What happened when running Envy?  Did you try an automatic install latest ATI driver?  Did it say your hardware was compatible?

I initially tried xserver-xgl (which worked), but xgl seems to use a lot of processor all the time.

Envy installed the latest ATI driver for me, I uninstalled xgl, and then made a couple of edits to xorg and usr/bin/compiz.  A reboot later, et voila....

[http://ubuntuforums.org/showpost.php?p=3950616&postcount=3](http://ubuntuforums.org/showpost.php?p=3950616&postcount=3)

---

### Post by tiger.woods on 2008-01-16
If I remember it said my hardware was not compatible - not an actual ENVY problem but it just gives the appearance of not working well...

I just don't understand why it's not as simple as just installing the ATI driver and away we go...

danwood76,

I tried Method 1 with negative results, after installing xorg-driver-fglrx modifying the xorg.conf to use fglrx as the driver and rebooting, black screen and no desktop...

I guess I'll give Method 2 a go...

TW,

---

### Post by ugm6hr on 2008-01-16
> **tiger.woods said:**
> If I remember it said my hardware was not compatible - not an actual ENVY problem but it just gives the appearance of not working well...

I just don't understand why it's not as simple as just installing the ATI driver and away we go...


Envy didn't *look* like it worked on mine either.  But I just had to remove xgl and the ATI Catalyst config tool started working.  Of course, if it said that your card was not supported - then your card must be too old for direct ATI support.  Envy just locates and downloads the latest driver from the ATI website.

It *should* be that simple, but it looks like your hardware may not be supported?

If it was going to work - this would be how: [http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

---

### Post by tiger.woods on 2008-01-16
OK, I followed process2 fom this link ([http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)) and it all seemed to go according to plan until the reboot..

The driver compiled and seemed to install without a hitch on reboot I have the following messages with just a black screen...

Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/.....) = sda3(8,3)
kinit: trying to resume from /dev/disk/by-uuid/...
kinit: No resume image, doing normal boot...

Ubuntu 7.10 laptop tty1
login:


Somehow I think the Xorg.conf is a little jacked up... I see 2 device sections trying to load the "ati" driver and another section trying to load "fglrx" driver??

Section "Device"
    Identifier "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]
    Driver      "ati"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier    "aticonfig-Device[0]
    Driver         "fglrx"
    Option        "VideoOverlay" "on"
    Option         "OpenGLOverlay" "off"
EndSection

Any thoughts?

---

### Post by tiger.woods on 2008-01-17
This is looking more and more like an xorg.conf problem... 

When manually trying to start x from the CL I get the error "no screens found"?

Just changing the driver in the Device section and adding the Options seem to be causing the problem:

	Driver		"fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"

So I went back to the ATI driver in and x started and ran the following.

buntu-laptop:~$ fglrxinfo
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

---

### Post by tiger.woods on 2008-01-17
I've attached both of the xorg.conf files one before the ATI driver install and one after, you can see where it seems to be jacked up... looking for some hints or ideas??

From the new xorg.conf:

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by tiger.woods on 2008-01-18
Have I come to a dead end on this? any other suggestions from anyone?

TW,

---

### Post by danwood76 on 2008-01-18
I doubt you are going to get the new ati driver working with your card.
Your best bet is to use the open source ati driver.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

thats a link from the community pages, follow that and you may be able to get desktop effects working.

regards,
Danny

---

### Post by dabigjones on 2008-01-26
hey there i had the same problem with this graphics card. But someone in the german (yes i'm german what explains my probably quite bad english) comunity explained to me that the card hasn't enough video ram to show use compiz in 24 bit. So the solution is to enter the xorg.conf and change the part "DefaultDepth 24" to 16. Then after reboot you can try this order "SKIP_CHECKS="yes" compiz --replace" in the console. Then compiz should start. If it works then create the file "~/.config/compiz/compiz-manager" and fill in the line "SKIP_CHECKS="yes". Now compiz should be running on startup. But with my system there was now a problem watching videos, dvb-t and pöaying openarena. So until i know something better i hve to change the color depth to 24bit and deactivat compitz from the menu to view movies. Maybe you can translate the german thread for helping you, too / [http://forum.ubuntuusers.de/topic/147812/](http://forum.ubuntuusers.de/topic/147812/) )

---

