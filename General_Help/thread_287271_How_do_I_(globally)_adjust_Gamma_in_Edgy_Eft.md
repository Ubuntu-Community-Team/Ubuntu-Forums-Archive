---
title: "How do I (globally) adjust Gamma in Edgy Eft?"
date: 2006-10-28
forum: General Help
---

### Post by ropers on 2006-10-28
Does anyone know how I can adjust gamma in Edgy Eft? 

I have a fairly old 15 inch CRT monitor which is kinda dark, even with the brightness control turned all the way up. 
On Dapper Drake I had a tool named SiSCtl installed (I use a SiS630 based system). 
I used to use that tool to increase the global gamma value, thereby making everything brighter without colour distortion. That tool got uninstalled during the Edgy upgrade. I could prolly reinstall it, but I'm wondering if there's another way, eg. by editing some system config files? 

(The downside to using the SiSCtl tool was that I had to do it again every time I rebooted; the changes were not persistent.)

---

### Post by ropers on 2006-10-28
I think I might have solved the issue myself by reinstalling SisCtrl from [http://www.winischhofer.eu/linuxsispart4.shtml#download](http://www.winischhofer.eu/linuxsispart4.shtml#download) (go to section [5. Debian and Ubuntu]) and then clicking on the Current tab inside the SiSCtrl app and editing /etc/X11/xorg.conf (sudo vi /etc/X11/xorg.conf) to include the additional values given there. This is what I included in my xorg.conf:
```

Section "Monitor"
	Identifier "Generic Monitor"

	# Gamma correction 
	Gamma 1.700 1.700 1.700
EndSection

Section "Device"
	Identifier "Silicon Integrated Systems (SiS"

	# Now for the real thing:
	Driver "sis"

	# EnableSiSCtrl must be set to use SiSCtrl
	Option "EnableSiSCtrl" "yes"

	# [sisctrl] Enable/disable Gamma correction for CRT1
	Option "CRT1Gamma" "on"

EndSection
```

---

