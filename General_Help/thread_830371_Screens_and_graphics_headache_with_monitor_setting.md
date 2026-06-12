---
title: "Screens and graphics headache with monitor settings :("
date: 2008-06-15
forum: General Help
---

### Post by stevieP on 2008-06-15
Today I tried to install a 2nd monitor to extend my laptop to a dual monitor set-up. My attempt failed miserably, and now I seem to be stuck in what is either low-graphics mode or a lower resolution setting than my monitor is capable of. 

WHAT I HAVE:

I am running Gutsy on a Dell XPS laptop, so I don't know if this post should go into the Desktop Environments forum, the Dell support forum, or here..

According to my computer spec sheet, I have a 15.4 inch Wide Screen WXGA TrueLife LCD  monitor


WHAT I DID:

I went into Administration-> Screens and Graphics -> Screen 2 -> clicked Secondary Screen-> Model -> Viewsonic VX900, etc... and either clicked Test or OK, I suppose I must have clicked OK for my settings to be changed. 


WHAT HAPPENED:

It did not work. I then got a message that said:

"UBUNTU IS RUNNING IN LOW-GRAPHICS MODE
Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself."


WHAT I TRIED TO REPAIR THE SITUATION:

I then gave up on trying to get dual monitors to work, and tried to save my original screen settings. When I went to Screen 1 -> Model -> Detect , all it found was "Generic Plug 'n' Play". The graphics driver was set to vesa. 

Everything else I've tried fails to configure. Even when I click the "Wide-screen" button with the Generic Plug 'n' Play monitor it fails to configure. 

In my /etc/X11/ directory I even tried:

%  sudo cp xorg.conf xorg.conf.disaster
%  sudo cp xorg.conf.failsafe xorg.conf

(Restart)

And I still have same crappy low-res monitor settings (maybe 800x600). 

What can I do to restore the original settings of my screen? There must be a simple fix for this. Please help if you have any suggestions...

StevieP

---

### Post by theparticle010 on 2008-06-15
Alright dude... gutsy is old... I know that there are warnings about hardy... but it's a lot better than gutsy... unless you have an acer... ( they overheat like mad ) so upgrade first... and forget your monitor... that is unless you are and advanced user. And if you are an advanced user take a look at this thread: [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

^_^

---

### Post by theparticle010 on 2008-06-15
Also... I've had the same problem... you'll need to reinstall your system. :(

---

### Post by stevieP on 2008-06-15
> **theparticle010 said:**
> Also... I've had the same problem... you'll need to reinstall your system. :(

Seriously? :confused:

I've installed a lot of payware such as Matlab, and done a lot of customization such as changing the emacs interface, etc. Won't I lose all of this (and have to re-customize everything) with a system reinstall? There must be a better way...

---

### Post by stevieP on 2008-06-15
OK I may have saved myself a lot of pain.. For some reason my system saved a file in /etc/X11/ called xorg.conf_backup_200805182145
I do not know why or when this backup was made. 

but: 
% sudo cp  xorg.conf  xorg.conf.go_away
% sudo cp  xorg.conf_backup_200805182145  xorg.conf

did the trick. Now my display looks like it did before. I am still holding my breath but things seem to be working normally. 

I was getting ready to beg a Dell XPS user to send me their working xorg.conf file, which apparently would have also solved the problem. 

FYI here are the differences between the working xorg.conf [color=blue](in blue)[/color] and the non-working one [color=red](in red)[/color]:

[COLOR=Red]
Section "Module"
        Disable         "dbe"
        Disable         "dri"
        Disable         "glx"
        Disable         "vbe"
EndSection
[/COLOR]
[color=blue] (nothing in working xorg.conf) [/color]

In section "InputDevice"	
Identifier	"Synaptics Touchpad":

[color=red]	Option		"HorizScrollDelta"	"0" [/color]
[color=blue]	Option		"HorizEdgeScroll"	"0"[/color]

[color=blue]

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
[/color]
[color=red]
Section "Device"
	Identifier	"Failsafe Device"
	Driver		"vesa"
[/color]
[color=blue]
Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GT]"
	Driver		"nv" [/color]
[color=red]
Section "Monitor"
	Identifier	"Failsafe Monitor"
	Option		"DPMS"
EndSection [/color]
[color=blue]
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection [/color]
[color=red]
Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth	16
		Modes   "800x600"
	EndSubSection
EndSection
[/color]
[color=blue]
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600M GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1280x1280"

	EndSubSection
EndSection
[/color]

I wonder if another Dell XPS (M1530) user wouldn't mind posting their working xorg.conf file?... 

StevieP

---

### Post by stevieP on 2008-06-18
> **stevieP said:**
> For some reason my system saved a file in /etc/X11/ called xorg.conf_backup_200805182145
I do not know why or when this backup was made. 

% ls -Ftl

confirms that was made a month ago, for some unrelated reason. So I was just lucky I guess...

---

