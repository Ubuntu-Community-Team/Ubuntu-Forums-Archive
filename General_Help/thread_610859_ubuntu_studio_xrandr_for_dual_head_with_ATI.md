---
title: "ubuntu studio: xrandr for dual head with ATI"
date: 2007-11-12
forum: General Help
---

### Post by kensuguro on 2007-11-12
Been trying to get a working ubuntu studio setup working the past few days, and I can figure out how to edit the xorg.conf to auto setup xrandr for a normal dualhead setup. (screen 2 on the right)  I'll post my xorg.conf once I get home, but has ANYONE got an ati board to work?  I use radeon 9600.

What happens is, if I delete xorg.conf, xrandr shows both VGA and DVI output.  I can manually configure everything just fine with xrandr.  Then, when I edit xorg.conf, I only get 1 ouput called "default" which isn't mentioned anywhere in my xorg.conf.  I'm wondering if anyone can post a working xorg.conf for reference.

---

### Post by briwood on 2007-11-12
I'm not an X-pert, but:

You don't want to delete xorg.conf.  If you did and you don't have a back up of the orginal file that you can just copy back, I think you should follow these instructions to create a new xorg.conf: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973). I believe this part

>  sudo dpkg-reconfigure xserver-xorg

creates a new xorg.conf for you.


You can't copy just anyone's xorg.conf.  They need to have the same video card and maybe monitor that you do for their setup to be applicable.

Search these forums for xrandr. Vicky Lanburn has some good posts here. You'll might look at [http://lilserenity.wordpress.com/2007/10/30/outputswitcher-02-much-improved/](http://lilserenity.wordpress.com/2007/10/30/outputswitcher-02-much-improved/) too.

---

### Post by kensuguro on 2007-11-12
well, the xorg.conf not being there isn't the problem.  Let me say this again more clearly.  When I delete xorg.conf, everything runs fine.  Xrandr detects both outputs (VGA-0 and DVI-0) and I can control the outputs through xrandr just fine.  I re-copy my original xorg.conf, and everything is fine except xrandr now only sees one output, called "default".  The outputs aren't misplaced or anything, xrandr can only see one output.  Since xrandr runs fine without the xorg.conf, I am assuming xorg.conf is messed up. (according to xrandr, but ubuntu runs fine)

I am not trying to copy someone else's xorg.conf.  I am just trying to see the structure as reference.  Please read the original post.

---

### Post by kensuguro on 2007-11-12
here's the video related portion of xorg.conf:

```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"monitor-VGA-0" "monLeft"
	Option		"monitor-DVI-0" "monRight"
EndSection

Section "Monitor"
	Identifier	"monLeft"
	Option		"PreferredMode" "1280x1024"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"monRight"
	Option		"PreferredMode" "1280x1024"
	Option		"RightOf" "monLeft"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Monitor		"monLeft"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"
		Virtual 2560 1024	
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

and this is what xrandr shows:
```

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      75.0*    70.0     60.0  
   1152x864       75.0     70.0     60.0  
   1024x768       75.0     72.0     70.0     60.0  
   1024x480       60.0  
   848x480        60.0  
   800x600        75.0     72.0     70.0     60.0     56.0     47.0  
   720x576        60.0  
   720x480        60.0  
   640x480        75.0     72.0     60.0  
   640x400        75.0     60.0  
   512x384        60.0  
   400x300        75.0     60.0  
   320x240        75.0     60.0  
   320x200        75.0     60.0  
   2560x1024      75.0  

```

What I don't understand is, where is this "default" display coming from?  And why doesn't xrandr see the two outputs as VGA-0 and DVI-0 anymore?  I can post the response from xrandr when I boot without xorg.conf if it helps.

One thing I noticed is that Ubuntu Studio has a "Screen Resolution" system preference tool, and the choice of 1280x1024 at 75hz seems to reflect the setting in "Screen Resolution".  I'm suspecting that somehow, the preference tool may be overriding the settings in xorg.conf, or swapping it during load..  not sure.

---

### Post by reacocard on 2007-11-12
I think the issue may be that you're using the 'fglrx' driver in your xorg.conf, which doesn't support xrandr. when you delete xorg.conf, X falls back to the 'ati' (I think, might be 'radeon') driver, which does support xrandr.

---

### Post by kensuguro on 2007-11-13
I think you've hit jackpot buddy!  Now dual head works perfectly untill I log in. So, I'm pretty sure that the xorg.conf is right, but perhaps ubuntu studio is loading in preferences of its own.

This is what I get from xrandr:
```

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024
VGA-0 connected 1280x1024+0+0 (normal left inverted right) 338mm x 270mm
   1280x1024      60.0*+   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DVI-0 connected 1280x1024+0+0 (normal left inverted right) 338mm x 270mm
   1280x1024      60.0*+   59.9  
   1152x864       74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right)

```

And I'm not sure how I can set the screen size to 2560x1024 since that doesn't show up in gnome preference's resolution tool.  Any guesses?  I remember 2560x1024 used to show up on the list, but not anymore..  this is very confusing.

---

### Post by reacocard on 2007-11-13
> **kensuguro said:**
> I think you've hit jackpot buddy!  Now dual head works perfectly untill I log in. So, I'm pretty sure that the xorg.conf is right, but perhaps ubuntu studio is loading in preferences of its own.

This is what I get from xrandr:
```

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024
VGA-0 connected 1280x1024+0+0 (normal left inverted right) 338mm x 270mm
   1280x1024      60.0*+   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DVI-0 connected 1280x1024+0+0 (normal left inverted right) 338mm x 270mm
   1280x1024      60.0*+   59.9  
   1152x864       74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right)

```

And I'm not sure how I can set the screen size to 2560x1024 since that doesn't show up in gnome preference's resolution tool.  Any guesses?  I remember 2560x1024 used to show up on the list, but not anymore..  this is very confusing.

you can set it manually with xrandr, I think this should work:
```
xrandr --output DVI-0 --right-of VGA-0 --mode 1280x1024
```
if that works, just add that to your startup in system->preferences->sessions and you'll be all set.

---

