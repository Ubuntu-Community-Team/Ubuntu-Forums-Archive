---
title: "Slow Scrolling under Hardy- Firefox, PDF files, OpenOffice..."
date: 2008-05-02
forum: General Help
---

### Post by Serpentinsek on 2008-05-02
I've just upgraded to Hardy 8.04 LT from 7.10 and I can't believe how slow the scrolling is while listing trough a PDF document in the default PDF browser or scrolling down a web page in FireFox 3 Beta.

**Can someone please help me to fix this problem?**

I've also found some old threads about the same problem:
[http://ubuntuforums.org/showthread.php?t=708928](http://ubuntuforums.org/showthread.php?t=708928)
In this thread there is a small fix to this problem by configuring this file
```
/etc/X11/xorg.conf
```

Can someone read the second post in the mentioned thread and show me how to configure my file?

When I open it, this is what I get under "section Device"
```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection
```

---

### Post by ghostknife on 2008-05-02
Have you tried the first option/suggestion in the mentioned thread?

If you have, you can configure X by editing the file "/etc/X11/xorg.conf". Do this by running the following command:
**sudo gedit /etc/X11/xorg.conf **

Please remember to first make a backup copy. Do "cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup" 
Edit the file, save and exit.

Thereafter you need to restart X. Easiest way is just to restart the machine. if that doesn't work, try changing your driver to vesa. If this breaks your system, and you end up at the console, just login and use the console to fix the driver by doing: "cp /etc/X11/xorg.conf.mybackup /etc/X11/xorg.conf" and restart your machine again.

If you don't know how to edit in the console, learn that first. Gedit won't work if X doesn't start up.

---

### Post by ghostknife on 2008-05-02
I had the same problem after upgrading to 8.04.

I tried the Theme solution in the previous one and it helped a lot. Not perfect yet though.

---

### Post by Serpentinsek on 2008-05-02
Thank you for your reply!

I've edited my /etc/X11/xorg.conf file like stated below:


```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
        Option		"AccelMethod"		"xaa"
EndSection
```

I restarted my computer and the same slow perfromance during scrolling **was still there**.

I have a laptop prestigio nobile 157 w/ ATI Radeon Mobility 9700

---

### Post by Serpentinsek on 2008-05-02
> **ghostknife said:**
> I had the same problem after upgrading to 8.04.

I tried the Theme solution in the previous one and it helped a lot. Not perfect yet though.
Can you tell me more about this?

---

### Post by ghostknife on 2008-05-02
OK. I seemed to fix it perfectly, by doing the following.

Goto "System"->"Preferences"->"Appearance". Then select your desired theme, and click the "Customize" button.

In the Controls tab select the "Simple" option. This makes scrolling work perfectly for me.

I am going to try to find a way to get the controls to look better while still getting fast scrolling, but for the mean time you can try this.

---

### Post by Serpentinsek on 2008-05-02
> **ghostknife said:**
> OK. I seemed to fix it perfectly, by doing the following.

Goto "System"->"Preferences"->"Appearance". Then select your desired theme, and click the "Customize" button.

In the Controls tab select the "Simple" option. This makes scrolling work perfectly for me.

I am going to try to find a way to get the controls to look better while still getting fast scrolling, but for the mean time you can try this.
nope ... didn't work for me ...:confused:

---

### Post by ghostknife on 2008-05-02
Hey,

Finally figured it out.

It seems to be a problem with Firefox 3.

The latest nightly build fixed the problem for me.

[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.0pre.en-US.linux-i686.tar.bz2]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.0pre.en-US.linux-i686.tar.bz2")

Or 64bit:
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.0pre.en-US.linux-x86_64.tar.bz2]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.0pre.en-US.linux-x86_64.tar.bz2")

You can also try "www.getfirefox.com" to try FF2 (or through synaptic package manager).

Also do the xorg configuration options in the other thread. I have the one with the EXA and greedy options selected.

It seems this will fix the scrolling in the rest of the system, and then the latest firefox will fix it's own bugs.

Note that the nightly build will probably not allow much of your plugins to work. So FF2 might be a good option if you need some that doesn't work. You can also try running them side by side if that would work for you.

---

### Post by Serpentinsek on 2008-05-02
So is this the right way to configure my xorg.conf file?


```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
       [COLOR="Red"] Option		"AccelMethod"		"exa"
	Option		"ExaNoComposite"	"true"
	Option		"MigrationHeuristic"	"greedy"[/COLOR]
EndSection
```

But I'm also talking about other apps, not just Firefox ... nautilus, Openoffice, PDF browser ... All these have the same problem.

---

### Post by Serpentinsek on 2008-05-02
I've also tried with an edited xorg.conf file that I posted in my previous post.

**Can someone please help me with this problem**, looks like I'm not the only one.

At least please help me with an eazy way to go back to gutsy, because things were doing fine under 7.10

Thank you in advance.

---

### Post by ghostknife on 2008-05-03
I MIGHT be mistaken here, but the EXA xorg.conf configuration seems to be only for intel drivers.

Slow scrolling... hmmmm... This is a difficult one, I was hoping to receive the same problem as you did after upgrade so I can experience it first hand and figure it out.

The fact that all scrolling is slow for you is probably because of your device driver. Try up/downgrading it. Also try using the opensource one (radeon instead of fglrx). I've never really worked with rendering/xorg drivers, so this process might involve a lot of failed experiments.

It would be nice to narrow it down. Do you have any QT applications? See if they scroll slowly as well. If not it's probably GTK related.

Also try running glxinfo, fglrxinfo, and the ATI control center. See if there is anything out of the ordinary. Is direct rendering on? Acceleration? AGP speed, etc. It seems there are some problems related to this in 8.04. 

One more, please paste your whole xorg.conf. (Remember code tags).

---

### Post by ghostknife on 2008-05-03
> **Serpentinsek said:**
> 
At least please help me with an eazy way to go back to gutsy, because things were doing fine under 7.10


None. Sorry. Best to do is to fix it or install 7.10.

---

### Post by Serpentinsek on 2008-05-03
> The fact that all scrolling is slow for you is probably because of your device driver. Try up/downgrading it. Also try using the opensource one (radeon instead of fglrx). I've never really worked with rendering/xorg drivers, so this process might involve a lot of failed experiments.
Sorry, for not letting you know sooner, but I don't know how to install a driver on linux.

> It would be nice to narrow it down. Do you have any QT applications? See if they scroll slowly as well. If not it's probably GTK related.
Opera is a Qt application, right? Well, right now I'm using opera and it is also slow.

> Also try running glxinfo, fglrxinfo, and the ATI control center. See if there is anything out of the ordinary. Is direct rendering on? Acceleration? AGP speed, etc. It seems there are some problems related to this in 8.04. 
Any guidelines? When I ran glxinfo via command line, my screen just crashed and I had to restart.

> One more, please paste your whole xorg.conf. (Remember code tags).

Here it is ...
[http://pastebin.com/m568ea75e]("http://pastebin.com/m568ea75e")

Oh, and another thing - video via VLC or TOTEM player dosent work smooth but it's like watching a slideshow.

Thank you ghostknife for your replys and all your future ones:)

---

### Post by ghostknife on 2008-05-03
OK. It sounds like there is definitely something wrong with your screen driver.

It's either the driver that is having problems, or some Xorg modules that has incompatibilities. It's possible that the Ubuntu team was a little to eager to put in beta software. They didn't test many of the Radeon cards with the drivers. From what I've read around the net this was a time pressured early release. If this is true, I'm very disappointed. (Added: I mean, my system just crashed!!! Very disappointed. 7.10 didn't give me any problems.)

Either way. Try using the open source driver. In xorg.conf change:
```

Section "Device"
        Identifier      "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

```

TO 

```

Section "Device"
        Identifier      "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
        Driver          "radeon"
        Busid           "PCI:1:0:0"
EndSection

```

See if that makes a difference. If you're X refuses to start after this, make sure you know how to edit it in the console. (Ctrl+Alt+F1 twice).
Then login and use "sudo" with a console editor like vim or nano to edit /etc/X11/xorg.conf with a console editor. If you don't know how to do this, first ask and I'll instruct you. Make sure you know how to do this, as you won't have display if X doesn't start with the radeon driver, and unless you have another machine you won't be able to get help then.

---

### Post by Serpentinsek on 2008-05-03
> **ghostknife said:**
> 
See if that makes a difference. If you're X refuses to start after this, make sure you know how to edit it in the console. (Ctrl+Alt+F1 twice).

I know how to use console commands but when do I press - Ctrl+Alt+F1

Can you please correct me if I'm wrong?

First edit my file like this: (will nano work under console only interace?)
```
$ sudo nano /etc/X11/xorg.conf
```
Than i restart ...

If it dosent work ...
```
$ cd /etc/X11/
$ sudo cp xorg.conf.backup xorg.conf 
```

Is this what you have in mind?

---

### Post by ghostknife on 2008-05-03
Yes, that's fine. You press Ctrl+Alt+F1 when X doesn't start and you still can't see a console. Sometimes this happens, mostly you will see one though.

If Ctrl+Alt+F1 doesn't work, you press it but leave F1 and press it again, so it's basically, hold Ctrl+Alt and press F1 twice, then leave Ctrl+Alt.

Anyway, doing an xorg.conf backup is perfect. Edit it, restart X (logout and press Ctrl+Backspace).

If it doesn't work restore the backup and restart X/machine again.

Sorry for the late reply. I've been busy today.

---

### Post by Serpentinsek on 2008-05-03
Well ... It didn't work. When I logged id w/ the modiefied file everything was going even slooooooower and than I backuped my old one and I'm back to slow scrollin Hardy version. I think I'm going to downgrade to gutsy.

---

### Post by spudratic on 2008-05-03
just curious go to system, administration,system monitor and see if evolution data sever is using a lot of cpu if it is and you don't use evolution mail end the data sever and see if that helps(if this helps alwasy check again at reboot to see if it starts again if it does end the process again.Also download seamonkey from the repo works %300 then firefox 3.5 beta it even works better than any firefox in the repo and does not crash on you tube or at least it hasn't yet for me.funny on this hardy release video,audio and web surfing are no where near as good as gusty on my system.funny a average type user would only use audio,video and web surfing.It's going to be a quick try for these peeps and back to windows I would guess.Also pulse audio gives me lag so I switched vlc to use alsa that helped also with the system lag,Some times I have to switch back to pulse to get audio on some sopcast and shoutcast channels,which I did not have to do in gusty.one more thing my cpu runs hotter with hardy than gusty.Ya think they would have released a fix for the evolution data sever pegging the cpu.I think I'm going to dump this hardy os and go back to gusty for the time being till some can fix the kernel,pulse audio,and firefox gets out of beta which really is no guarantee fire fox sucked on the last 2 releases so who knows.

---

### Post by ghostknife on 2008-05-03
It must be a kernel problem then. Maybe it is doing something your radeon driver doesn't like.

Is DRI enabled?

---

### Post by Serpentinsek on 2008-05-03
Hey,

right now I'm back to 7.10 Gutsy and everything works fine! Compiz, video,  smooth scrolling ... everything!

So now I have another question. How the hell am I going to find out when this problem is going to be solved for hardy?

Anyway: **ghostknife - thank you very very very much for all your fast feedback! THANK YOU!**

---

### Post by spudratic on 2008-05-03
I'll be keeping  it on my hard drive and I'm going to install 7.10 in a different partition pm me from time to time Serpentinsek I am going to continue to keep an eye on it and play with it.Hopefully the first round of updates will help.

---

### Post by Serpentinsek on 2008-05-03
Thx! I will do so!

---

### Post by ghostknife on 2008-05-04
Spudratic? You got the same problem, ie. slow scrolling everywhere? And when rendering graphics it renders very slowly.

---

### Post by spudratic on 2008-05-04
yes ghostknife.Running intel p4 2ghz with 2 gigs of ram and the intel 845g chipset.evo data sever was killing me pegging the cpu so I killed itthat was one prblem.fire fox is another just touching the scroll wheel will peg the cpu usage.Now i use seamonkey,this is rock solid on utube and flash sites and did not crash one time.My windows preview plugin leaves the windows on the screen till I rotate the cube or over write the screen with another window to make them go away.Scrolling in most anything has lag.My video lags with compiz off in gusty I could keep it on and had very little video trouble.I think this lag is some how connected to pulse audio.when I switch vlc alsa it gets better but not as good as gusty.I'm going to wait for the first round of updates to see what it corrects and take it from there.I followed the development of hardy and intel.Intel was going to be fully supported so I figured video would be better in hardy but gusty worked better for me.awn and screenlets installed my cpu will boot but gives a error and awn or screenlets won't start at boot.I tried to update from gusty first that failed right at the end when it booted things were crashing all over the place so I did a clean install and have the problems above and more so I installed it again and get the same problems every time.All i can do now is wait and see thanks for asking ghostknife.

---

### Post by spudratic on 2008-05-05
ok here is what I found.my cpu doing nothing and I mean nothing every 30 seconds spikes to 100 percent for 10 seconds.this is what is causing lag and I don't know why 0r what is doing it any ideas.the system monitor is not showing the cpu use as far as what is doing it.It shows the system moitor and during the spike of cpu use the monitor is only between 50 and 60 percent in the process list and that is all it shows where is the other 40% comming from for the ten seconds every 30 seconds.I think it the kernel.any ideas any one thank you.

---

### Post by spudratic on 2008-05-07
Serpentinsek I just found out I don't have enough posts yet to pm so I putting the info here in hopes that you will see it.there have been lots of updates over the past three days and they helped alot but it still lags for me a little.I would wait a little while longer to upgrade.It still needs a little more polishing I think.

Edit:I will post here from now on to keep you up to speed.

---

### Post by divali on 2008-05-24
Still waiting for a concise solution to the problem of slow scrolling
in Hardy. It's a sad let down for what could have been a pretty good upgrade. The Hardy frustrations continue.

---

### Post by divali on 2008-05-24
Ok. Got it.
Do:  System>Preferences>Appearance and reduce Visual Effects to None. It's sad to lose the effects but, it does do the trick.

---

### Post by defe007 on 2008-05-27
I have the same problem as Serpentinsek and its getting really frustrating.  I didn't have this problem in 7.10.. I'm thinking of downgrading until this issue is solved.  Here's my information, maybe it will contribute to a solution...

I am running Ubuntu 8.04 on a laptop.
1.7 GHz Intel Centrino
1 GB RAM
ATI Mobility Radeon 9700 Pro (fglrx driver)

Here is my fglrxinfo output:
```
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)
```

I thought this was odd... Shouldn't this be the proprietary driver, aka ATI instead of Mesa?

Here is my xorg.conf file:
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

I also get a ticking/squeaking noise from my CPU when attempting to scroll in Firefox, PDF viewer, etc.. I believe its caused by the before mentioned CPU spikes caused by scrolling.

> **divali said:**
> Ok. Got it.
Do:  System>Preferences>Appearance and reduce Visual Effects to None. It's sad to lose the effects but, it does do the trick.

This solution does not work for me :(

Anyways, thanks for listening and hopefully there will be a working solution soon.

---

### Post by defe007 on 2008-05-28
Hey guys, I think I have found a solution to this problem, at least for myself.  My problem was that my graphics card driver/render kept on reverting back to Mesa which caused all my slow scrolling problems.

I installed the ATI driver with Envy and followed the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers") and removed my xserver-xgl, which I used in the previous Ubuntu builds to get Compiz to work.  Hopefully this solution will work for some of you.

---

### Post by m42tyger on 2008-12-31
> **divali said:**
> Ok. Got it.
Do:  System>Preferences>Appearance and reduce Visual Effects to None. It's sad to lose the effects but, it does do the trick.

this fixed my cpu-spike/scrolling problem! thx :KS

would have thought the medium range effects would be handleable by my mid-range laptop + 7.04, but alas i guess it wasn't. 

however, EVERYTHING is faster now, nice and snappy. i think i'll leave the fancy effects to macs and vista. :P

---

### Post by jwhiteheadcc on 2009-01-09
That last trick with reducing visual effects to [none] really helped me.  Thanks everyone!

I'm going to install ATI's drivers to hopefully get visual effects and the full human theme working at normal speeds.  I seriously thought that my CPU was running at 200MHz instead of 2000MHz.  That or they used a QBASIC-style interpreter.  ;)
Using better drivers should also let me try TA:Spring on my 64-bit system.

Info:
AMD Athlon 64 (socket 939)
Gigabyte K8N Pro SLI (nForce chipset family)
1GB PC3200
64-bit 8.04 Hardy with minor tweaks for WinE, CD burning, and some programming tools.

---

