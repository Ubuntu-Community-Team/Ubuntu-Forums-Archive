---
title: "Tonka game with Wine"
date: 2006-12-25
forum: General Help
---

### Post by Hiroshima on 2006-12-25
I need a little help.  My son got a game for Christmas "Tonka Search and Rescue 2".  Unfortunately, it's for Windows, and so I tried installing Wine with Synaptic.  As far as I know, Wine is working ok.

The problem comes when I try to load the game.  It looks like it is starting, and then the screen goes black and freezes.  The arrow curser is still there.  If I don't have the CD in the tray, it reminds me (with a windows looking window) that I need the CD for the game.

Looking at Wine HQ, it says that the game will not load, but that information was from 2004:
[http://appdb.winehq.com/appview.php?iAppId=1939](http://appdb.winehq.com/appview.php?iAppId=1939)

I read somewhere that running from terminal "wine Tonka.exe" is a good idea because you can see any errors in terminal, but since it blacks out the whole screen, and I have to logout or shutdown, the terminal isn't there again when I start up... is there a way to look at terminal history to look at the errors?

Thank you,

Hiroshima

---

### Post by nikhilk on 2006-12-25
Try redirecting the output to a file. You can see the file after reboot etc.

```
wine Tonka.exe > ~/tonka.out
```

---

### Post by majoridiot on 2006-12-25
i think what you want to do (assuming that tonka.exe is in the PATH or you are in that
directory) is the following:

```
 wine Tonka.exe > ~/Desktop/wine.err 2>&1
```

which will run the tonka game and re-direct the errors to the file wine.err on your desktop, for
easy double-click viewing.

---

### Post by Hiroshima on 2006-12-25
Thanks for the responses.  I will try when I get home, and then let you know what errors I get.  I did shorten the path for the purposes of the post... 
it was something like 
wine ~/.wine/C/InteractiveGames/Tonka.exe ... but I will have to double check that when I am at my own computer.

Thanks again,

Hiroshima

---

### Post by Hiroshima on 2006-12-26
Just about to try with:
 wine /home/hiroshima/.wine/drive_c/Program Files/Infogrames Interactive/TONKA Search & Rescue 2/TONKA.exe > ~/Desktop/wine.err 2>&1
 

The path being to the game being:
 /home/hiroshima/.wine/drive_c/Program Files/Infogrames Interactive/TONKA Search & Rescue 2/TONKA.exe

---

### Post by Hiroshima on 2006-12-26
Now I'm confused.  I tried from that path, and the response in terminal was that it couldn't find the file... I cut and copied the path from the launcher on the desktop... which looks like the right path.  I tried putting a [COLOR="Red"]\[/COLOR] in when there was a space in the path name, like > drive_c/Program[COLOR="Red"]\ [/COLOR]Files but it still couldn't find the file.  I double checked all the cases matched... and still not there. I can see it if I navigate to the file in nautilus.

Any ideas?  I'll play around a little more myself too.

---

### Post by Hiroshima on 2006-12-26
Ok, I did play around a little more.  I removed the spaces from the path and it worked. The path is now: > ~/.wine/drive_c/Program_Files/Infogrames_Interactive/TONKA_Search/Tonka.exe 

and so I entered in terminal:
> wine ~/.wine/drive_c/Program_Files/Infogrames_Interactive/TONKA_Search/Tonka.exe > ~/Desktop/wine.err 2>&1

That gave me:
> fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1af228) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x18e908)->(0x10024,00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_WAIT flag right now.
err:ntdll:RtlpWaitForCriticalSection section 0x510370 "?" wait timed out in thread 0009, blocked by 000e, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x510370 "?" wait timed out in thread 0009, blocked by 000e, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x510370 "?" wait timed out in thread 0009, blocked by 000e, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x510370 "?" wait timed out in thread 0009, blocked by 000e, retrying (60 sec)

I don't know what to do from there.

Thanks in advance,

Hiroshima

---

### Post by nikhilk on 2006-12-26
It seems to be emanate from the Wine API. I guess you should try the Wine forums for help.

---

### Post by majoridiot on 2006-12-26
> **Hiroshima said:**
> I don't know what to do from there.


the first three errors are unimplemented API functions... not much you can do about that
for now.  they might very well be non-fatal.  some wine apps i run spew FIXME's left and right
but still run well.

> **Hiroshima said:**
> fixmerandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16

this looks like it is failing to change color depth from from 32 to 16.  make sure you have
16 bit color enabled in your monitor definitions in /etc/X11/xorg.conf.

---

### Post by Hiroshima on 2006-12-26
Thanks for the ideas.  When I get home I will check the wine forums and also my colour depth.

Cheers,

Hiroshima

---

### Post by Hiroshima on 2006-12-27
> **Hiroshima said:**
> Thanks for the ideas.  When I get home I will check the wine forums and also my colour depth.

This is what the xorg.conf said:
> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade XPAi1"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection
How do I edit the file... just in make changes is Gedit and save?  Which changes should I make?

Sorry for asking what are probably basic questions,

Hiroshima

---

### Post by majoridiot on 2006-12-27
ok, you do have 16 bit depth available (from the "Screen" section):

```
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
```

one thing to try is to make lower 16 bit depth resolutions available, as i'm betting that game will want at least 800x600.  
change the above to read:

```
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
```

and then ctrl-alt-backspace to resart the x server (be sure to save any open files before).

if it still errors on the depth change, you might also try changing the default depth for X.

```
Section "Screen"
Identifier "Default Screen"
Device "Trident Microsystems CyberBlade XPAi1"
Monitor "Generic Monitor"
DefaultDepth 24
```

this:
```
Section "Screen"
Identifier "Default Screen"
Device "Trident Microsystems CyberBlade XPAi1"
Monitor "Generic Monitor"
DefaultDepth 16
```

ctrl-alt-backspace to restart x again and see if that changes anything.

(and don't forget about the change to the default depth when you're done, as it will start at 16 bit until you change it back to 24)

---

### Post by Hiroshima on 2007-05-18
Majoridiot, thanks for all the suggestions.  I never did get it working, and I didn't realize until now that you left a post that I hadn't responded to.  Bad manners, I appologize.

I thought I would give it another try today.

Cheers for now, 

Hiroshima

---

