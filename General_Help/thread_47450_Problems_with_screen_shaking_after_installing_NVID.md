---
title: "Problems with screen shaking after installing NVIDIA drivers"
date: 2005-07-08
forum: General Help
---

### Post by GreyFox503 on 2005-07-08
I'm having problems with my screen shaking after installing my graphics card drivers.  I am using Ubuntu 5.04, an AMD AthlonXP, Geforce 6800 GT card, and a Samsung 710t LCD monitor.

I installed NVIDIA drivers using the instructions here:  [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

The installation went fine, but when I booted the computer the next time, the screen was vibrating just slightly, it didnt move a lot, but it was enough to give me a headache if i stared at it for too long.  When I went to Applications > System Tools > NVIDIA Settings, my screen went black for a moment, then the NVIDIA window appeared and my screen was cured!  Unfortunately, it went back to its old behavior every time I logged back out (including at the login screen).

So after trying a few different things, I set my monitors refresh rate to 60hz instead of 75hz (the default).  That worked great to fix it, but my login screen is now constantly jittery, though it stops when I log in.

Here are my questions:
1)  Do you think I fixed the cause of the problem by changing refresh rates, or is there something else that could be wrong?
2)  Depending on #1, how can I get my welcome screen to stop shaking?

Thanks for reading such a long boring post.  By the way I am a proficient Windows user who is a complete linux noob.  But I'm having a pretty good Ubuntu experience so far making the switch.

EDIT: spelling correction.

---

### Post by GreyFox503 on 2005-07-08
Update:  I seemed to have fixed this problem by using

sudo dpkg-reconfigure xserver-xorg

and choosing "nv" instead of "nvidia".


No need to reply.

---

### Post by GreyFox503 on 2005-07-13
UPDATE:

To let others who have this problem know how I went about finally solving this.

After choosing "nv" instead of "nvidia" as my driver, I later realized that I could not run 3d applications, and the GLX test refused to run:

```
glxgears
```

So I switched back to the nvidia drivers by editing the /etc/X11/xorg.conf file

My desktop was fine, but my GNOME login screen's refresh rate was too high (it was 75Hz, I wanted 60) and so it was vibrating.  Here's the relevant section of my final xorg.conf:

```

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	262144
	Option		"UseFBDev"		"true"
[B]	Option "HSync2" "63.80"
	Option "VRefresh2" "60.00"[/B]

EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	**HorizSync	30-64**
#	VertRefresh	56-75
#	VertRefresh	56-110
EndSection

```

The bolded lines were the crucial changes I had to make to get my GNOME login screen to finally behave.  I tried adding the modeline and VertRefresh changes, but they did not help.

---

