---
title: "ThinkPad T42 Ubuntu Installation"
date: 2008-05-05
forum: General Help
---

### Post by lattmau on 2008-05-05
Hi, 

I'm planning to install Ubuntu on my ThinkPad T42.  Is anyone familiar with what packages I can install that are tailored towards ThinkPads to achieve full ThinkPad functionality?  For example, the hard drive active protection, hotkeys, power management?  Thanks

---

### Post by chchandler on 2008-05-07
Bump... 

And, I'm planning on a fresh install of HH on a used T42 I have on the way.  I'll report on what my experience was, but I'm pretty new with Linux.

---

### Post by chchandler on 2008-05-09
OK, the used T42 arrived last night.  It had only enough DOS left to get to a C:\ prompt.  I booted it up with the 8.04 CD in the drive at 9:53 pm.  Twenty-nine minutes later I was looking at the CNN homepage via my wireless network.  So far, everything I have tried has worked out of the box except:
Had to add NTP to sync the clock
Had to add Flash plug-in
Had to add Java plug-in
The track-scroll thingie (not sure of the name... the blue button that will scroll when used with the red button in the keyboard) doesn't work, but I have seen a fix for that.
Had to install a codec to play a DVD

So far, so excellent!

---

### Post by lattmau on 2008-05-09
compiz worked out of the box for you?  i still can't get it working

---

### Post by Whiffle on 2008-05-09
> **chchandler said:**
> OK, the used T42 arrived last night.  It had only enough DOS left to get to a C:\ prompt.  I booted it up with the 8.04 CD in the drive at 9:53 pm.  Twenty-nine minutes later I was looking at the CNN homepage via my wireless network.  So far, everything I have tried has worked out of the box except:
Had to add NTP to sync the clock
Had to add Flash plug-in
Had to add Java plug-in
The track-scroll thingie (not sure of the name... the blue button that will scroll when used with the red button in the keyboard) doesn't work, but I have seen a fix for that.
Had to install a codec to play a DVD

So far, so excellent!

Excellent.  [www.thinkwiki.org](www.thinkwiki.org) is a very very useful site for thinkpads.  Any questions just ask.

---

### Post by chchandler on 2008-05-09
> **lattmau said:**
> compiz worked out of the box for you?  i still can't get it working

Haven't tried it unless it's part of the default install.  This one has the ATI 9600 video chipset, but haven't tried anything with video beyond what was installed by default.

Also, the center button scroll was a simple fix, from
[http://aaltonen.us/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/](http://aaltonen.us/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/)
A matter of editing xorg.conf just as he says, logging out and logging back in.  

So far so good!

---

### Post by penguinszp on 2008-07-13
I just recently installed Ubuntu 8.04 on my T42 but have been nervous about using it frequently because I didn't think any active protection came with the install. Does it actually come with this protection and I'm just oblivious, or did you get it somewhere?

And I saw your post about getting the tracker point to work, and don't quite know how to do it on mine. I'm still really new at all this, any help would be much appreciated.

Thanks

---

### Post by chchandler on 2008-07-14
Unfortunately, there does not seem to be any Linux APs yet.  Still, most laptops don't have that and there does not seem to be a major problem...

Hard Drive Active Protection: The new ThinkPads are equipped with IBM&#8217;s patented hard drive protection technology. The IBM Active Protection System detects system acceleration like that which occurs in a fall or sudden move and responds by temporarily parking the drive&#8217;s head. This feature can save your hard drive in the event of a fall or sudden impact. The IBM drivers for Windows display the system status and show a nifty graphical representation of your ThinkPad in motion. Unfortunately, there is no support for Linux yet.

For the blue scroll button:

For those of us who use the award-winning TrackPoint pointing device, it&#8217;s handy to use the center, blue button for scrolling functionality. In Windows, this is taken care of by IBM&#8217;s drivers, but in Linux we can enable this feature by some editing of xorg.conf.

Open /etc/X11/xorg.conf in the text editor of your choosing, and add the following two lines to the appropriate InputDevice section (see my xorg.conf below):

    Option           &#8220;EmulateWheel&#8221;
    Option          &#8220;EmulateWheelButton&#8221;    &#8220;2&#8243;

Restart X and you should be able to press the center, blue button and use the TrackPoint as a scroll wheel.

To re-start X, just log out and log back in.

HTH...

---

### Post by penguinszp on 2008-07-14
I got the TrackPoint working again, thanks =). And I haven't had any problems with the missing active protection, so I think it will be fine for now. I'll keep an eye out for it though

---

### Post by Windnsea26 on 2008-07-23
Hello everyone,
I am a happy new Ubuntu user and have got everything working but the center scroll button that seems to plague most Thinkpad users.  I have a T42P with Ubuntu 8.04 installed. 
I have followed the instructions located here:  [http://aaltonen.us/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/#scrolling](http://aaltonen.us/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/#scrolling)

I then saved the file, restarted but still can't seem to scroll. Here is my xorg.conf file:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Driver		"fglrx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option    	"EmulateWheel"        "true"
	Option    	"EmulateWheelButton"  "2"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection




Am I missing something here?

Thanks for your help.

---

### Post by chchandler on 2008-07-23
Try this...


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"EmulateWheel"
	Option		"EmulateWheelButton"	"2"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

I think it's only the mouse section that needs 2 lines added.  the touchpad section looks ok at first glance.

---

### Post by Windnsea26 on 2008-07-23
I dunno what is different now than what I was doing before but I took your advice and my scroll is working:)  Now all I gotta do is figure out how to do the VPN thing and I can take on Ubuntu without Windows!

Thanks for the help

---

