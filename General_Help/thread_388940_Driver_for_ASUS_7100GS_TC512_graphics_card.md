---
title: "Driver for ASUS 7100GS TC512 graphics card?"
date: 2007-03-20
forum: General Help
---

### Post by YoungCthulhu on 2007-03-20
Gidday,

I am a newbie and in need of some help again... This time with my graphics driver card, which does not seem to work with Google-earth.  Following the recommendations on the Google-earth site I downloaded a package of drivers:

	NVIDIA-Linux-x86-1.0-9755-pkg1.run

and ran the script (?) from Terminal with the X server turned off.  It didn't work. :confused: 

I have an ASUS 7100GS TC512 PCIE card and I have also tried to download a Linux driver for it from [www.asus.com](www.asus.com).  The link is here:

[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=EN7100%20Series](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=EN7100%20Series)

It seems that they don't supply a Linux driver. Does anybody know of a substitute Linux driver that I can use that Google-earth will accept?  

In case the answer lies closer to home, here is a part of what is reported by "lspci"

	02:00.0 VGA compatible controller: nVidia Corporation Unknown device 016a (rev a1)


This is a part of my /etc/X11/xorg.conf file

	Section "Monitor"      
		Identifier      "ADI F72&#65533;&#65533;&#65533;&#65533;&#65533;"
	#       Option          "DPMS"
	        HorizSync 30-70
	        VertRefresh 50-120
	EndSection
	Section "Device"
	        Identifier      "NVIDIA Corporation NVIDIA Default Card"
	        Driver          "nv"
	        BusID           "PCI:2:0:0"
	EndSection


As this is a new computer with an old HP M70 CRT screen I had to do some tweaking to get it to work on higher resolution.  In response to my earlier call for help on this forum I was advised to add the  lines:
 
	HorizSync	30-70
	VertRefresh	50-120

and to comment out the line:

	Option "DPMS"

This worked a treat and I can now set my sceen to 1280 x 1024 resolution!:) 

I was also advised to enter "Monitor 0" for Identifier, but it would not boot up; the "ADI F72?????" is what was there originally before I started messing around with it!  Likewise substituting "Driver nvidia" for "Driver nv" prevents the X server from starting ](*,) .

 
Is the problem in my xorg.conf file or do I need a different driver?  I would be greatful for your suggestions!

Cheers

:confused:

---

### Post by mcduck on 2007-03-20
Forget about Asus, it's just another nVidia card. I recommend using the Envy script to install nVidia drivers for you.

---

