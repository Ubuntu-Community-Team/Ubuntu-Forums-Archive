---
title: "Diablo II and Wine and Xorg and ..."
date: 2008-02-18
forum: General Help
---

### Post by lastredoubt on 2008-02-18
EDIT:: The below still may be the source of the problem, yet I recently stumbled across a minor success. I can get the game to run but in a really small window.  Is there any way I can increase the window size or play it fullscreen?  I managed to get this far by either running the game via terminal with a '-w' at its end or by clicking the windowed option in winecfg.  The screen is a little too small to play on still, so please help! Not sure if this helps but here is my xrandr output:

> 
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 347mm x 260mm )  *60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none


It seems like I've tried everything to get this to work.  Well hopefully not everything.  

I've been trying to get Diablo II(plus LoD expansion) to work under wine 0.9.53 and Ubuntu 7.04 on my Toshiba satellite A10 with Intel Corporation 82852/855GM Integrated Graphics Device. I followed the extremely helpful howto found floating on these forums and have tried several xorg configurations.  Suffice to say that it isn't working. The problems I've encountered seem numerous, but also seem to revolve around a central issue. It is that issue I would appreciate help with.  I will try to provide as much information as possible. 

In simple terms, the diablo video test comes up with no video modes found (exclamation mark) and the game itself comes up with good old error 22: a critical error has occurred with DirectDraw.  Here's what it looks like in Terminal:

> arthur@hieronymous:~$ wine /home/arthur/.wine/drive_c/Program\ Files/Diablo\ II/Diablo\ II.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
ALSA lib seq_hw.c:457: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
arthur@hieronymous:~$ libGL warning: 3D driver claims to not support visual 0x4b
fixme:win:EnumDisplayDevicesW ((null),0,0x34e474,0x00000000), stub!
err: x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x8 @0! (XRandR)


[quick note that two spaces exist up there that aren't there in my terminal -- I just made them to get rid of smiley faces]  Okay, so going back a few steps, here's what it looks like when I run the video test:

> arthur@hieronymous:~$ wine /home/arthur/.wine/drive_c/Program\ Files/Diablo\ II/D2VidTst.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:win:EnumDisplayDevicesW ((null),0,0x33e11c,0x00000000), stub!

And going back a few more steps to my xorg.conf file, which I have tried several times to reconfigure, both automatically and manually, now looks like this --  well at least the part I think matters:

> Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

I would like you to note that I have tried the game and the test with the vesa driver (which xorg reconfigure automatically chooses) and the current i810.  Following one howto on the ubuntu wiki pages I tried changing the driver to 'intel' but that destroyed my computer and I had to change it back to one of the two options above. 

So basically, to cut a long winded story short, I've been trying to gather as much information as I can to help myself but according to all those tidbits I seem to be doing everything right and it still isn't working.  Could anyone out there help?  I know you can! 

As a further note, the response to  glxinfo | grep direct is rendering: Yes. 
Oh, and glxgears works fine. Just fine.

Thanks in advance for any and all help!

---

