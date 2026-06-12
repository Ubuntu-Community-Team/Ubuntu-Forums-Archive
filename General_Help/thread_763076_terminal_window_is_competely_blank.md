---
title: "terminal window is competely blank"
date: 2008-04-22
forum: General Help
---

### Post by thedoorguy on 2008-04-22
I'm running ubuntu 7.10.  

When I open Terminal (application> Assessories) all I get is a white window with nothing in it. 

I tried to un-install terminal thinking maybe a reinstall would fix the problem but it won't let me.

Any idea how to fix it?  


Thanks,  thedoorguy aka Richard

---

### Post by Anduu on 2008-04-23
Try changing the text/background colors.Maybe you've got white text on a white background somehow.

---

### Post by thedoorguy on 2008-04-23
> **Anduu said:**
> Try changing the text/background colors.Maybe you've got white text on a white background somehow.

I changed the setting in System > Appearance and that didn't fix it.  I don't know how to text/background colors in just the terminal window.  I just recently installed and haven't learned my way around much yet. 

I notice this morning... well, I have a microsoft keyboard that among other things has a volume control on it... yesterday when used, a small window opened with a speaker icon and slide bar showing an increase/decrease.  Today that window is blank.

don't know if that relates to terminal window or not.

Thanks much for your help!!  Additional assistance will be greatly appreciated!!

thedoorguy aka Richard

---

### Post by Anduu on 2008-04-23
Right click anywhere in the terminal window...a menu will pop up.

Select "Edit current profile".From there you have access to change colors.

---

### Post by mali2297 on 2008-04-23
Try another terminal emulator, you should have xterm installed by default.
Open the run dialog (Alt+F2) and type
```

xterm

```
Does it work?

---

### Post by thedoorguy on 2008-04-23
> **mali2297 said:**
> Try another terminal emulator, you should have xterm installed by default.
Open the run dialog (Alt+F2) and type
```

xterm

```
Does it work?

Hey... that opened a terminal window with a black background. The other one still comes up blank white.  (and the background and text colors are not the same,)

But hey.... I've got a terminal... it is linux again .... far out!!

Many many times Thank You to both you mali2297 and you anduu!!

Maybe someday even I will be smart enough to help someone on this forum. Not. lol

thedoorguy aka Richard

ps.  I put in a support request on the issue on launchpad today (*30546) so maybe that will also yield something.

---

### Post by mc4man on 2008-04-23
do you have an nvidia card using restricted drivers/

---

### Post by thedoorguy on 2008-04-25
> **mc4man said:**
> do you have an nvidia card using restricted drivers/

Yes I do.  Is that doing something weird?

(man...what is going on with the forum site... I tried all day to get on and couldn't?)

Thanks,   thedoorguy

---

### Post by | MM | on 2008-04-25
try restarting, see if fsck runs... i have issues where the term wouldn't display and fsck has found filesystem errors.  When they are fixed things are ok again.

---

### Post by thedoorguy on 2008-04-25
> **| MM | said:**
> try restarting, see if fsck runs... i have issues where the term wouldn't display and fsck has found filesystem errors.  When they are fixed things are ok again.

I've restarted many times since problem first appeared.  It persists.  How do you tell if fsck has run?

Also, recently, I un-istalled the terminal thru Synaptic which also un-installed desktop. I reinstalled desktop which reinstalled terminal.  The problem persists.

Thanks, thedoorguy

---

### Post by mali2297 on 2008-04-25
Since xterm works, I would guess that the problem is related to gnome-terminal. What happens if you start gnome-terminal from xterm? 
```

gnome-terminal

```
Any error messages?

---

### Post by mc4man on 2008-04-25
I remember reading a bug report which I can't locate and may not be applicable in your case (was from feisty I believe). In any event the fix was to add Option		"AddARGBGLXVisuals"	"True" to xorg.conf. Ex.
```
Section "Device"
	Identifier	"NVIDIA GeForce 7800 Gs"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
        Option "DynamicTwinView" "False"
        Option		"AddARGBVisuals"	"True"
        Option		"AddARGBGLXVisuals"	"True" 
```

---

### Post by mali2297 on 2008-04-25
Here is an old bug report: 
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/127887](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/127887)

> 
Does running the command "grep -i AddARGBGLXVisuals /etc/X11/xorg.conf"
in a termanal result in the output:
    Option "AddARGBGLXVisuals" "True"?

If it does not give that output, then you need to run "sudo
nvidia-xconfig --add-argb-glx-visuals". Next time you restart, it
should work.


---

### Post by thedoorguy on 2008-04-25
> **mali2297 said:**
> Since xterm works, I would guess that the problem is related to gnome-terminal. What happens if you start gnome-terminal from xterm? 
```

gnome-terminal

```
Any error messages?



That opens the blank white window.  No error message.

thedoorguy

---

### Post by thedoorguy on 2008-04-25
> **mali2297 said:**
> Here is an old bug report: 
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/127887](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/127887)

FAR OUT!!!!   That fixed it!  Not only that...  it restored the title bar to windows with the action boxes in the rt corner that had disappeared somewhere alone the way.

I can't THANK YOU two enough for your help!!!  Having the title bars back will be even nicer day to day than having terminal back.

THANK YOU!!

thedoorguy   aka   Richard

---

### Post by Jeneral22 on 2008-05-24
Mali's bug report fix worked for me. 


Thank you everyone. I didn't notice at the time but I had actually lost the min/max/close at the tops of all open windows also. That was also fixed with this. I assume this is an issue with NVidia cards only? 

take care

---

### Post by JPBodner on 2008-06-18
I'm having a similar problem:

When I open terminal, and type a command (example: ls) some of the output characters are visible, some are not.  When I highlight the screen with my mouse, they appear.   I've check the terminal settings, colors, etc.  

I can run x-term successfully.  When I run gnome-terminal from Alt-f2, it seems to be working ok.  

Here's the trick: I'm on a radeon graphics card, not nvidia.  

Any ideas?

---

