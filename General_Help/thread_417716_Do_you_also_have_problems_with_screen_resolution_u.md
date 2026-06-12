---
title: "Do you also have problems with screen resolution under Feisty?"
date: 2007-04-21
forum: General Help
---

### Post by BrokeBody on 2007-04-21
Before I installed proprietary nVIDIA drivers, when I went to System-> Preferences-> Screen Resolution, I had a resolution at 1024x768 on 85Hz. Just like it's supposed to be. After installing proprietary nVIDIA drivers, my resolution was still at 1024x768, but on 50Hz. I switched that on 85Hz in nvidia-settings and when I went to System-> Preferences-> Screen Resolution to check it out, it was on 100Hz. Every time I make changes in nvidia-settings, I save them (/etc/X11/xorg.conf), and every time I restart X, it's always back on 50Hz at 1024x768 resolution.

MSI StarForce Geforce4 MX440 64MB

---

### Post by SargeZT on 2007-04-21
Wow, I just posted pretty much the same thread. My eyes are really hurting because I can't figure out a way to change it.

---

### Post by SargeZT on 2007-04-21
If it's worth noting, I too have an NVidia card. 6800GT. 3D Acceleration is working fine, though.

---

### Post by SargeZT on 2007-04-21
Oh, and it just gets weirder. It's running at 85hz even though the 65hz options is the largest one that appears on 800x600, the only slightly usable resolution.

---

### Post by dualscreenman on 2007-04-21
Did you configure your monitor?

It often won't give you good configuration ranges if you don't.

---

### Post by DoktorSeven on 2007-04-21
Does Ubuntu (Feisty or general) have some sort of GUI or other way to set monitor refresh rates, anyway?  Going in and putting the HorizSync/VertRefresh settings in xorg.conf isn't very user-friendly, and I would think that would be a necessary step for many people.  After I installed, for example, the screen was stuck at some horribly low resolution (800x600 or maybe lower!) at 60Hz, and I had to set these in xorg.conf.

If such a thing doesn't exist, maybe this needs to be added.  Many other distros have a way to select your monitor from a list and/or insert HorizSync/VertRefresh rates into a GUI.

---

### Post by samwyse on 2007-04-21
There's a GUI, but I think it's broken for nvidia proprietary drivers. I have a weird problem with resolutions too: [http://ubuntuforums.org/showthread.php?t=335237](http://ubuntuforums.org/showthread.php?t=335237)

---

### Post by Dave54 on 2007-04-21
I have the same problem of mis-matched refresh rates. I'm following a few other threads:
[http://ubuntuforums.org/showthread.php?t=415893]("http://ubuntuforums.org/showthread.php?t=415893")
[http://ubuntuforums.org/showthread.php?t=416679]("http://ubuntuforums.org/showthread.php?t=416679")
[http://ubuntuforums.org/showthread.php?t=414287]("http://ubuntuforums.org/showthread.php?t=414287")
I'll post if I find a solution.

---

### Post by BrokeBody on 2007-04-21
[QUOTE=DoktorSeven]
Does Ubuntu (Feisty or general) have some sort of GUI or other way to set monitor refresh rates, anyway?
[/QUOTE]

As I already said, I was trying to make changes in nvidia-settings (it's a GUI application), and when I click on "Save" button, it's making monitor changes to the xorg.conf.

---

### Post by stokedfish on 2007-04-21
No, I don't.

---

### Post by DoktorSeven on 2007-04-21
> **BrokeBody said:**
> As I already said, I was trying to make changes in nvidia-settings (it's a GUI application), and when I click on "Save" button, it's making monitor changes to the xorg.conf.

That was actually more of a general question, not a direct reply to you.  It's true that the nvidia-settings and the general screen resolution settings is always at odds, but I tend to ignore them by just setting the resolution/monitor sync settings in xorg.conf.  I was just wondering if there was a GUI that could set these without hand-editing xorg.conf, and if not, why.

---

### Post by BrokeBody on 2007-04-21
But I wasn't hand-editing, although changes have been made to xorg.conf.

---

### Post by DoktorSeven on 2007-04-21
> **BrokeBody said:**
> But I wasn't hand-editing.

Right.  Again, I wasn't talking about your particular situation.

Linux handles resolutions and refresh rates primarily by the xorg.conf configuration file (in /etc/X11); it holds all screen resolutions that the display will switch to, and something called "HorizSync" and "VertRefresh", which describe how fast your monitor refreshes itself.  From those, it tries to set the maximum possible resolution from the screen resolution list, and computes the highest refresh rate from that resolution and the given HorizSync and VertRefresh.  

(A little oversimplified, but you get the idea.)

The GUIs you're seeing likely change the screen resolution after the fact -- X can change modes to any other valid mode on the fly by using something called RandR (sets screen size, orientation, and reflection).  Apparently the GUIs are not getting the correct (current) information from this, and displaying the wrong thing.

In other words, my rant is more general in getting Ubuntu configured correctly in the first place; yours is getting the GUIs to act right.   Sorry to cross the wires here, but one does have to do with the other, in the end.

---

### Post by SargeZT on 2007-04-21
> **DoktorSeven said:**
> Right.  Again, I wasn't talking about your particular situation.

Linux handles resolutions and refresh rates primarily by the xorg.conf configuration file (in /etc/X11); it holds all screen resolutions that the display will switch to, and something called "HorizSync" and "VertRefresh", which describe how fast your monitor refreshes itself.  From those, it tries to set the maximum possible resolution from the screen resolution list, and computes the highest refresh rate from that resolution and the given HorizSync and VertRefresh.  

(A little oversimplified, but you get the idea.)

The GUIs you're seeing likely change the screen resolution after the fact -- X can change modes to any other valid mode on the fly by using something called RandR (sets screen size, orientation, and reflection).  Apparently the GUIs are not getting the correct (current) information from this, and displaying the wrong thing.

In other words, my rant is more general in getting Ubuntu configured correctly in the first place; yours is getting the GUIs to act right.   Sorry to cross the wires here, but one does have to do with the other, in the end.

Well, I get what you're talking about if that's any consolation, and I agree. It's annoying, and you think at this level of maturity Ubuntu would have these things nailed, but unfortunately it does not. Don't get me wrong, not slamming it, but it would be nice not to have to browse at 800x600 :p

---

### Post by comfortablynumb on 2007-04-22
Yep, same problem, I'm done pulling my hair out....it is what it is I guess..

FWIW I have a Geforce 2 GTS in my Ubuntu box.

---

### Post by JohanL on 2007-04-22
I have this too. I have changed the xorg.conf more times than I want to remember. I am at the point now were I can go into nvidia-settings, change the settings to 1280x1024 at 75 hz were I want them. Works fine. On reboot, however, it reverts back to 60hz. On the login screen after a reboot its actually still at 75 hz, but as soon as I am back on the desktop its 60hz...

Had no problems with this on Edgy. Very irritating.

I have a GeForce 6600.

---

### Post by Dr_Deadmeat on 2007-04-22
You can count me in on the resolution problems under feisty...

I have a nvidia geforce 4 420go with 16megs of ram

You can fix the problem if you change to the 'nv' driver instead of your 'nvidia' driver, but at least I lost my 3d acceleration when I did that, so I will rather try to fix the resolution problem... Please give me a pm or post in this thread if anyone finds an answer on this problem.

---

### Post by Psychomechanix on 2007-04-22
Hiya

I was having the exact same problem and it was because I wasn't doing a "sudo" when I called up the NVidia control panel. If you don't do a SUDO then it won't save the settings even though you clicked "Save settings" on the control panel.

sudo nvidia-settings

put in your password, make changes then click the save settings button on the control panel.

Hope that helped.

---

### Post by BrokeBody on 2007-04-22
[QUOTE=Psychomechanix]
I was having the exact same problem and it was because I wasn't doing a "sudo" when I called up the NVidia control panel. If you don't do a SUDO then it won't save the settings even though you clicked "Save settings" on the control panel.

sudo nvidia-settings

put in your password, make changes then click the save settings button on the control panel.
[/QUOTE]

Still same thing. :( Every time I restart X, it's back on 50Hz.

---

### Post by HG3 on 2007-04-22
> **BrokeBody said:**
> Before I installed proprietary nVIDIA drivers, when I went to System-> Preferences-> Screen Resolution, I had a resolution at 1024x768 on 85Hz. Just like it's supposed to be. After installing proprietary nVIDIA drivers, my resolution was still at 1024x768, but on 50Hz. I switched that on 85Hz in nvidia-settings and when I went to System-> Preferences-> Screen Resolution to check it out, it was on 100Hz. Every time I make changes in nvidia-settings, I save them (/etc/X11/xorg.conf), and every time I restart X, it's always back on 50Hz at 1024x768 resolution.

MSI StarForce Geforce4 MX440 64MB

You are not alone. It seems many people are having this issue.

I'm having the same problem with the nVIDIA driver running clean install of Feisty and a Gforce 6200. 

I had a resolution of 1024x768 at 85Hz after the clean install. After installing the nVIDIA drivers, the highest resolution and refresh rate available from 'Preferences->Screen Resolution' was 1024x768 at 54Hz. Although my 20" LCD has a default resolution of 1280x1024 at 85Hz.

I ran 'sudo nvidia-settings' in the terminal and adjusted my resolution to 1280x1024 at 75Hz and saved the settings to the X configuration file. At this point everything seemed okay until a restart....

After a restart, the login screen seems to have the proper high resolution. But once I login the resolution goes back down to 1024x768 at 50Hz.

This issue really needs to be resolved as its very annoying.

---

### Post by JohanL on 2007-04-22
Glad to see its not just me being stupid. And yes, I did sudo nvidia-settings as well. Didn't help. The settings don't last over a reboot anyway.

Annoying!

---

### Post by Talon2 on 2007-04-22
> **BrokeBody said:**
> Before I installed proprietary nVIDIA drivers, when I went to System-> Preferences-> Screen Resolution, I had a resolution at 1024x768 on 85Hz. Just like it's supposed to be. After installing proprietary nVIDIA drivers, my resolution was still at 1024x768, but on 50Hz. I switched that on 85Hz in nvidia-settings and when I went to System-> Preferences-> Screen Resolution to check it out, it was on 100Hz. Every time I make changes in nvidia-settings, I save them (/etc/X11/xorg.conf), and every time I restart X, it's always back on 50Hz at 1024x768 resolution.

MSI StarForce Geforce4 MX440 64MB

Yes, I definitely have problems along these lines.

My refresh rate is stuck at 50hz.

I learned not to use nvidia-settings as it really messed things up with the xorg.conf it saved.

Still no solution.  Has anyone checked to see if this has been reported?

MSI Geforce 7600GS 256mb

---

### Post by Dave54 on 2007-04-22
I also have an nVidia card and the same problem. This is what I found:

No matter what you try, the nvidia settings will not stick. However, any choice you make in nvidia settings will also be in System > Preferences > Screen Resolution. But, there's a catch. nvidia settings will name the resolution correctly, while Screen Resolution Preferences will not. So, start with the correct resolution size you want, and then try each and every Hz level. Even though it says "56Hz", it may actually be 85Hz. After applying each resolution, check your monitor settings to see what the refresh rate it actually is.

Does anyone know a way to get terminal to print out your current resolution/refresh rate, for those who can't check it through their monitors?

Anyway, after finding the resolution in Screen Resolution Preferences, it will stick after a reboot.

Hope this helps!
-Dave

---

### Post by Animortis on 2007-04-23
I had a huge problem with Feisty's screen resolution and refresh rates - Far more than Edgy gave with the game hardware. I ended up hand-configuring the screen ranges based on settings my monitor gave me while I was logged in to Windows XP at my desired resolution. I intend to post a walk-through of what I had to do to get Feisty running so someone can fix it eventually, hopefully with a patch or something. I'm still not using the Nvidia drivers on my Nvidia 7600 - just Vesa.

---

### Post by Dr_Deadmeat on 2007-04-23
I got things to work with [this](http://ubuntuforums.org/showthread.php?t=417188) thread, but I believe that only works with a Toshiba Satellite 1410 series, although I am not sure...

(The url is [http://ubuntuforums.org/showthread.php?t=417188](http://ubuntuforums.org/showthread.php?t=417188), if the fancy clicky link didnt work)

EDIT: If you know something about editing the EDID-file it is possible to edit that file to your own needs, but I dont know how to do that...

---

### Post by Zeffel on 2007-04-23
> **Dave54 said:**
> I also have an nVidia card and the same problem. This is what I found:

No matter what you try, the nvidia settings will not stick. However, any choice you make in nvidia settings will also be in System > Preferences > Screen Resolution. But, there's a catch. nvidia settings will name the resolution correctly, while Screen Resolution Preferences will not. So, start with the correct resolution size you want, and then try each and every Hz level. Even though it says "56Hz", it may actually be 85Hz. After applying each resolution, check your monitor settings to see what the refresh rate it actually is.

-Dave

That worked for me, too. Thanks for posting the tip, Dave!

---

### Post by gfederas on 2007-04-24
I'm having the same problem with the nVIDIA driver after running a clean install of Feisty Fawn using Nvidia Geforce 6200, and have what I think is a related problem which hinders repair. I used Nvidia-glx drivers, and turned restricted module support on through System settings. BTW, taking out the Nvidia card and using the native Intel chipset works fine, but I get analog instead of DVI output.

The highest resolution w/ Nvidia was 800x600 w/ 52Hz, but the monitor can display up to 1920x1600 @ 60 Hz. I changed settings in Nvidia-Settings and got one more option to work - 1024x768. this resolution held after rebooting. menu bars are still off screen on all sides, and I can't pan around, only move the mouse off screen and see if a dialog box pops up into view.

The related problem: Terminal loads as a white screen with white text. I can't see what I type or what echos back unless I switch to a new TTY terminal. After making changes, I run /etc/init.d/gdm restart. Fixing this problem will make tracing down the other problems much easier. I can't reload Terminal through Synaptic. Any ideas?

---

### Post by CocoAUS on 2007-04-24
Screen resolution shouldn't be dependent on your graphics card or driver.  This is sort of hackish, but all you have to do to get native screen resolution is simply edit the xorg.conf as instructed [here]("http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#resolution").  From what I've been told, the problem has to do with the way some monitors present themselves to the computer.  Supposedly, the reason support for resolution varies is because some distros (like Fedora) are willing to accept "broken" reporting of the monitor information, while other distros (like Debian) refuse to acknowledge the poorly-reported information.  I don't know if that's true, but everyone I've pointed to the above how-to has had good results.

---

### Post by BrokeBody on 2007-04-24
Problem resolved. :)

Now it shows the proper refresh rate when I go to System-> Preferences-> Screen Resolution.

I added this at Section "Device" in xorg.conf:

Option "DynamicTwinView" "false"

```

So it now looks like this:

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	[COLOR="Blue"]Option "DynamicTwinView" "false"[/COLOR]
EndSection

```

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775)

---

### Post by JohanL on 2007-04-24
Thanks Dave54! Now it works! And stays after reboot. Hadn't occured to me to actually try those other settings...:rolleyes: 
BorokeBody, not sure if I dare to start changing things in xorg again, now that I can look at my screen again without going all dizzy. I'll try it, eventually.

---

### Post by BrokeBody on 2007-04-24
[QUOTE=JohanL]
BorokeBody, not sure if I dare to start changing things in xorg again, now that I can look at my screen again without going all dizzy. I'll try it, eventually.
[/QUOTE]

Well, on Launchpad, this is the actual solution for this *bug*. ;)

---

### Post by JohanL on 2007-04-24
OK you talked me into it. Changed it and it still works. And displays the correct refresh rate!

Thanks!

---

### Post by Dave54 on 2007-04-24
> **BrokeBody said:**
> Problem resolved. :)

Now it shows the proper refresh rate when I go to System-> Preferences-> Screen Resolution.

I added this at Section "Device" in xorg.conf:

Option "DynamicTwinView" "false"

:shock: :shock: :shock: 
I can't believe it! IT WORKS!!!! I've been searching for a solution for **6 months**. (I've had this problem since edgy.) I've been coming up with all sorts of little workarounds to help deal with the problem. Now I'm going to spread the word, the solution has been found!

Thanks a bunch!
-Dave

---

### Post by disturbedite on 2007-04-25
i've been using kubuntu since dapper and i've never had it perfectly detect my resolutions until ironically, feisty.  i didn't have to do anything.

---

### Post by dogson on 2007-04-25
I have that same problem, the montior is running at 85hz but the optiions in gnome displays 50hz...

---

### Post by BrokeBody on 2007-04-25
[QUOTE="dogson"]
I have that same problem, the montior is running at 85hz but the optiions in gnome displays 50hz...
[/QUOTE]

So, you haven't read whole topic. :p

[quote="BrokeBody"]
Problem resolved. :)

Now it shows the proper refresh rate when I go to System-> Preferences-> Screen Resolution.

I added this at Section "Device" in xorg.conf:

Option "DynamicTwinView" "false"

```

So it now looks like this:

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	[COLOR="Blue"]Option "DynamicTwinView" "false"[/COLOR]
EndSection

```

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775)
[/quote]

---

### Post by en3rgy on 2007-04-26
> **BrokeBody said:**
> Problem resolved. :)

Now it shows the proper refresh rate when I go to System-> Preferences-> Screen Resolution.

I added this at Section "Device" in xorg.conf:

Option "DynamicTwinView" "false"

```

So it now looks like this:

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	[COLOR="Blue"]Option "DynamicTwinView" "false"[/COLOR]
EndSection

```

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775)

Im sorry to ask this question but I am a n00b. What was the command you typed in Terminal to access that code and was there any special key combinations you used to save and reboot? Thank you so much!

---

### Post by disturbedite on 2007-04-26
well in nano (which is what i use from console/term) after editing a file the hotkey for saving is ctrl+o.  hope this helps.

---

### Post by peebly on 2007-04-26
Hello

Yes this fixed the screen resolution thing, but I noticed it caused nvidia-settings to display an error on one of the setting screens.

Still at least my monitor is set to the correct refresh rate.

---

### Post by peebly on 2007-04-26
> **en3rgy said:**
> Im sorry to ask this question but I am a n00b. What was the command you typed in Terminal to access that code and was there any special key combinations you used to save and reboot? Thank you so much!



sudo nano /etc/X11/xorg.conf

It may look nothing like the example posted, mine doesn't.

Add the option as posted in the example, its the line on blue.

Ctrl x, then y to save changes then press enter on the file name.

Be careful use at your own risk, you may break x.:mad: 

Ctrl - Alt - Backspace to restart x

---

### Post by dogson on 2007-04-26
> **BrokeBody said:**
> Problem resolved. :)

Now it shows the proper refresh rate when I go to System-> Preferences-> Screen Resolution.

I added this at Section "Device" in xorg.conf:

Option "DynamicTwinView" "false"

```

So it now looks like this:

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	[COLOR="Blue"]Option "DynamicTwinView" "false"[/COLOR]
EndSection

```

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775)

Thanks, this solved my problem!

---

### Post by dreamsayer on 2007-04-29
bump

---

### Post by dreamsayer on 2007-04-29
> **BrokeBody said:**
> Problem resolved. :)

Now it shows the proper refresh rate when I go to System-> Preferences-> Screen Resolution.

I added this at Section "Device" in xorg.conf:

Option "DynamicTwinView" "false"

```

So it now looks like this:

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	[COLOR="Blue"]Option "DynamicTwinView" "false"[/COLOR]
EndSection

```

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775)
I found this thread to apply this fix and have a question for someone. Why does my xorg device section look like:
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"

meaning it doesn't list the mfr. identifier info etc. Same for 
the monitor. Everything seems generic even tho my drivers work. I used Envy. Is there some program to run again to have this info auto-detected & populated in this config file?

---

### Post by Dave54 on 2007-04-29
> ...it doesn't list the mfr. identifier info etc. Same for the monitor. Everything seems generic even tho my drivers work. I used Envy. Is there some program to run again to have this info auto-detected & populated in this config file?
A while ago, I had run:
```
sudo dpkg-reconfigure xserver-xorg
```
During which it **did not auto-detect** that information, but rather it asked me to supply it. After that, the information was integrated into my xorg.

If your xorg is working fine, **do not run that command**. It will ask you all sorts of questions you don't know the answer to, then break your xorg.

At least, that's my experience ;)

---

### Post by TheDoulos on 2007-04-29
I followed that various suggestions in this thread, and I'm soooo close to getting this working.  The last snag I have is that my Login screen comes up in a strange low-res mode.  This isn't a problem in and of itself because I can still log in and then everything switches over to my selected screen resolution and refresh rate (1024x768@60).

The strange problem I have is when I'm on the login screen and I click on that menu icon on the left and try to select some other login option, the menu stays on the screen (overwriting the password entry area) and my system locks up.  I can still move the mouse around, but keyboard entry and mouse clicks do nothing.

Everything works fine with Edgy.

---

### Post by dreamsayer on 2007-04-29
> **Dave54 said:**
> A while ago, I had run:
```
sudo dpkg-reconfigure xserver-xorg
```
During which it **did not auto-detect** that information, but rather it asked me to supply it. After that, the information was integrated into my xorg.

If your xorg is working fine, **do not run that command**. It will ask you all sorts of questions you don't know the answer to, then break your xorg.

At least, that's my experience ;)

Could it be because I'm using a default Feisty install and the generic kernel? If I installed the linux-386 kernel and booted that would the hardware be detected and entered into the xorg file? I recall a few ubuntus back when I've used sudo-dpkg and my hardware for video card, monitor and mouse was correctly listed. Since edgy and now feisty not the case.

---

