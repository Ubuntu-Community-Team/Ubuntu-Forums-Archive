---
title: "Visual Effects in Hardy and ATI driver problems."
date: 2008-06-21
forum: General Help
---

### Post by whitedays81 on 2008-06-21
Hey everyone! I'm new to this forums, and im also new to ubuntu (and linux in general) i've just downloaded ubuntu 8.04 hardy. I've been trying to solve my problem for 2 days now, i've been to countless threads and HOWTO's. 

Anyways, When i set my Visual Effects to "normal" or "extra", i get a white screen for a few seconds, then it returns back to "none"

I've also tried "Envy" and "Hardware Drivers", It did install the driver, but it would not allow me to use Visual Effects.

The only way i can have Visual Effects when i use "sudo apt-get install xserver-xgl" but its unbearably slow, And scrolling on firefox becomes a pain. 

My video cards a "ATI Radeon x1650 Pro 512MB AGP"

Is there anyway i can use Visual Effects on Hardy with my ATI card? or should i downgrade to an older ubuntu? I really wanna get this out of my chest. its been bugging my for to long. :(

Many thanks in advance!

---

### Post by whitedays81 on 2008-06-21
Bumb, Can someone please help me? or direct me to a solution i have yet to try. i really wanna get the visual effects working.

I would really appreciate it!!!

---

### Post by startherepodcast on 2008-06-21
Ok, it really looks like you have not got any 3D accelerated graphics drivers in use.

Type ```
fglrxinfo
``` on the Terminal and it gives you something like not found you probably do not have the drivers.

What does the Hardware Drivers dialog say? Does it detect your card and suggest to install a driver?

If you do have the driver already, type

```
compiz --replace
```

on the Terminal to check whats wrong.

Just give me some more info, I am sure you can get it to work, because other people have too!

---

### Post by whitedays81 on 2008-06-21
> **startherepodcast said:**
> Ok, it really looks like you have not got any 3D accelerated graphics drivers in use.

Type ```
fglrxinfo
``` on the Terminal and it gives you something like not found you probably do not have the drivers.

What does the Hardware Drivers dialog say? Does it detect your card and suggest to install a driver?

If you do have the driver already, type

```
compiz --replace
```

on the Terminal to check whats wrong.

Just give me some more info, I am sure you can get it to work, because other people have too!

Thanks for the response!!!! :)

I've typed in "fglrxinfo" on the terminal, and it gave me this.

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```

On "Hardware Driver" it detected a "ATI accelerated graphics driver" and its "not in use" but when i enable it. i eather get the same problem but in 800 x 600 resolution, or just the same problem all together.

Also, i've tried "compiz --replace" it results in a white screen.

I've also use'd "compiz-check" heres what i got.

```
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon X1650 Pro (rev 9e)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

Everything looks ok. But i still cant use "Visual Effects". 

Please help.

---

### Post by whitedays81 on 2008-06-21
Bumb. sorry for double posting. 

Maybe if i post my xorg.conf, I'll get a solution.

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

Is there anything wrong here?

EDIT: forget it, i've updated upbuntu, and it crashed my system. I'm uninstalling ubuntu (maybe i'll downgrade later), its became a 3 day waste of time. thanks for replying guys. :)

---

### Post by Forlong on 2008-06-21
You have to decide whether you want to use the fglrx driver or not.

As you can see by the output of Compiz-Check, it would be working fine with the radeon driver that came with Ubuntu -- but since you still have the fglrx driver installed, Compiz won't run, because the fglrx module corrupts everything for you.

---

### Post by whitedays81 on 2008-06-21
> **Forlong said:**
> You have to decide whether you want to use the fglrx driver or not.

As you can see by the output of Compiz-Check, it would be working fine with the radeon driver that came with Ubuntu -- but since you still have the fglrx driver installed, Compiz won't run, because the fglrx module corrupts everything for you.

thanks for the reply.

how would i uninstall fglrx?

---

### Post by Forlong on 2008-06-21
That depends on how you installed it in the first place.

---

### Post by whitedays81 on 2008-06-21
> **Forlong said:**
> That depends on how you installed it in the first place.

To be honest, I never knew i had it installed. :(

---

### Post by Forlong on 2008-06-21
> **whitedays81 said:**
> I've also tried "Envy" and "Hardware Drivers"
That -- both -- would have installed the fglrx driver.

You said you "tried" both. Did it work both times? Did you un-install any of those?

---

### Post by whitedays81 on 2008-06-21
> **Forlong said:**
> That -- both -- would have installed the fglrx driver.

You said you "tried" both. Did it work both times? Did you un-install any of those?

Oh i see, Forgive me, I still pretty new. 

I've tried both of them separate and together. but Compiz didn't work.

---

### Post by Forlong on 2008-06-21
Well, that might be the problem already.

Let's try to fix this...
First, remove the fglrx driver that you can install via Ubuntu's repository (if still present):
```
sudo apt-get purge xorg-driver-fglrx
```
What does that command give you?

---

### Post by whitedays81 on 2008-06-21
> **Forlong said:**
> Well, that might be the problem already.

Let's try to fix this...
First, remove the fglrx driver that you can install via Ubuntu's repository (if still present):
```
sudo apt-get purge xorg-driver-fglrx
```
What does that command give you?

ok i installed a fresh copy of ubuntu. the "Hardware Drivers" bubble showed up to tell me to enable "ATI accelerated graphics driver" so i did. i rebooted, then it took me to the login, after that the screen just freeze. i can see and move my mouse, but nothings happening, right now im in "failsafe GNOME" posting this. 

heres what the terminal gave me after i use "sudo apt-get purge xorg-driver-fglrx"

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xorg-driver-fglrx*
0 upgraded, 0 newly installed, 1 to remove and 188 not upgraded.
After this operation, 30.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 95720 files and directories currently installed.)
Removing xorg-driver-fglrx ...
 * Stopping atieventsd                                                   [ OK ] 
Purging configuration files for xorg-driver-fglrx ...
dpkg - warning: while removing xorg-driver-fglrx, directory `/etc/ati' not empty so not removed.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

what should i do?

---

### Post by Forlong on 2008-06-21
Argh, no. :)
Now we have an absolutely different situation.
Please install that package again:
```
sudo apt-get install xorg-driver-fglrx
```
Then reboot.

Afterwards, go to *System &#8594; Administration &#8594; Hardware Drivers* and **disable** the driver.
Reboot again.

Finally run Compiz-Check again.


P.S. I'm going to watch the rest of the game now, so don't expect any further replies tonight. :)

---

### Post by whitedays81 on 2008-06-21
> **Forlong said:**
> Argh, no. :)
Now we have an absolutely different situation.
Please install that package again:
```
sudo apt-get install xorg-driver-fglrx
```
Then reboot.

Afterwards, go to *System &#8594; Administration &#8594; Hardware Drivers* and **disable** the driver.
Reboot again.

Finally run Compiz-Check again.


P.S. I'm going to watch the rest of the game now, so don't expect any further replies tonight. :)

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon X1650 Pro (rev 9e)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

Compiz-Check saids everything OK, but i get that horrible white screen when i set my Visual Effects on "extra" or "normal" so its right back to where i started. :(

but thanks for the support, and enjoy you're game. :)

---

### Post by darkshado on 2008-06-21
i have the same card no problem with de 3D effects, compiz run just fine! Try may be to use catalyst driver unstead from ubuntu repository. When i get a little time i post my xorg.conf.

---

### Post by brett123 on 2008-06-21
I don't claim to know very much at all, however I did spend weeks on getting visual effects and Compiz to work. Finally did, it was something stupidly wrong all along (blame Ubuntu install actually - but that'll start a flame war so I take it back)...

In my case, ALL that was wrong was:
System -> Admin -> Hardware Drivers and ensure any accelerator is enabled. 

Mine was not enabled as the message said "this isn't open source so screw you we're not enabling it" (something like that). Once I did enable it everything worked perfectly.

Posting this as a) it might help you, and b) it might remind other advanced users of something simple to check for with newbies before undertaking complicated fault finding. :D

---

### Post by whitedays81 on 2008-06-21
> **darkshado said:**
> i have the same card no problem with de 3D effects, compiz run just fine! Try may be to use catalyst driver unstead from ubuntu repository. When i get a little time i post my xorg.conf.

nice, posting you're xorg.conf would maybe help my problem. thanks!

> I don't claim to know very much at all, however I did spend weeks on getting visual effects and Compiz to work. Finally did, it was something stupidly wrong all along (blame Ubuntu install actually - but that'll start a flame war so I take it back)...

In my case, ALL that was wrong was:
System -> Admin -> Hardware Drivers and ensure any accelerator is enabled.

Mine was not enabled as the message said "this isn't open source so screw you we're not enabling it" (something like that). Once I did enable it everything worked perfectly.

Posting this as a) it might help you, and b) it might remind other advanced users of something simple to check for with newbies before undertaking complicated fault finding. 

My drivers "in use" and enabled as said by "Hardware Drivers", but i still cant set my "Visual Effects", i just keep getting the same blank screen, then back to nothing. :(

Im starting to become desperate, i might just downgrade till theres an ubuntu patch to make it easier for hardy users to use Compiz on ATI with no problem.

But i'm glad some of us managed to get it to work.:)

---

### Post by pietjanjaap on 2008-06-22
1 do this then compiz does not start with ubuntu, and you don't get the white screen.

Stop Compiz-Fusion From Loading Automatically

This guide will show you how to stop Compiz-Fusion from loading automatically on startup in Hardy Heron and how to setup a shortcut for launching Compiz when you want.

Step 1: Run gconf-edit
Start Run Application by pressing Alt+F2

Screenshot-Run Application

Enter gconf-editor into the box, hit enter


Step 2: Set Metacity as your default start up window manager
Once in gconf-editor navigate to desktop>gnome>applications>window_manager

Screenshot-Configuration Editor - window_manager

under current and default replace each instance of:
/usr/bin/compiz with /usr/bin/metacity
it should like this when you're done:

Screenshot-Configuration Editor - window_manager-1



Step 3: Create a shortcut for starting Compiz-Fusion
right click the Applications Places System Menu
select the Edit Menu option

Screenshot-Main Menu

pick a location for your shortcut and select New Item box

Screenshot-Launcher Properties
Type: Application
Name: Compiz
Command: compiz --replace
COmment compiz window manager


2 try this:
dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

3

/etc/modprobe.d/blacklist

hier in kopieren

blacklist i82875p_edac
blacklist edac_mc

4

Setup Compiz Fusion with open source ati radeon drivers

Older ATI cards have been blacklisted for Compiz Fusion because of a bug in the driver, but there is an easy workaround for many cards that use the open source ati drivers. Radeon 9500 are the oldest cards to support the restricted "fglrx" drivers, so everything older requires the open source drivers to function properly.



First edit the launcher for Compiz Fusion:

gksudo gedit /usr/bin/compiz

Near the top, add the line

SKIP_CHECKS="yes"

I added it under VERBOSE="yes"

You may also need to install the Compiz settings manager program that you can access from System->Preferences->Advanced Desktop Effect Settings | 1-click install or:

sudo apt-get install compizconfig-settings-manager

You can now load Compiz Fusion with

compiz --replace

and revert to Metacity (the basic window manager) with

metacity --replace

I suggest making launchers in a panel for this.

Remember that this is a workaround and may not work for everybody. If you have further problems, you should consider running a forum search and then posting on one of the main support forums if you still need help.
For the record, my card is an ATI Mobility Radeon 9000.

---

### Post by Forlong on 2008-06-22
> **whitedays81 said:**
> Compiz-Check saids everything OK, but i get that horrible white screen when i set my Visual Effects on "extra" or "normal" so its right back to where i started. :(
That's weird, because the white screen problem is generally limited to the fglrx driver.

Please post your current **/etc/X11/xorg.conf** as well as your **/var/log/Xorg.0.log**

---

### Post by Wildoat on 2008-06-22
I have the same problem - tried everything off the forums but still as soon as I enable desktop effects I get the 'white screen'. Have given up as many people seem to have it and it is beyond my neewbie status to carry on trying to fix it - have learnt to enjoy the simplicity of Hardy without it!! PS: ATI 9550 Card with fresh install of Heron. Maybe there will be a general patch/fix in time?

W

---

### Post by Forlong on 2008-06-22
> **Wildoat said:**
> ATI 9550 Card with fresh install of Heron
Did you try to install any drivers? Because your card should be able to run Compiz out-of-the-box.

In case you have a Hardy Live-CD, put it in and see if Compiz works for you there.

---

### Post by Wildoat on 2008-06-23
When 1st installed it asked me to use the restricted drivers which I did - re booted and white screen when I tried to enable 'normal' desktop. Then installed envyng and installed drivers that way and still get the same issue. I did install something as advised on the forum that allowed me to use effects but everything went so slow I took it off.

Its not desperate as everything works other than that.

W:)

---

### Post by Forlong on 2008-06-23
Still, you should boot a Live CD (make sure it's Hardy) and check if you are able to run the effects.

If you are (and I'm pretty certain that will be the case), you'll know that if you un-install the fglrx driver, you will be able to run Compiz.

---

### Post by Wildoat on 2008-06-24
> **Forlong said:**
> Still, you should boot a Live CD (make sure it's Hardy) and check if you are able to run the effects.

If you are (and I'm pretty certain that will be the case), you'll know that if you un-install the fglrx driver, you will be able to run Compiz.

Ok will download and cut a CD to run live CD - if as you say it is OK how would I un-install the fglrx driver and also should I stop using envyng to install ATI drivers?

Many thanks for your help.

W

---

### Post by Wildoat on 2008-06-24
Ran the live CD and whilst I didnt get the 'white screen' I got 'Desktop Effects Cannot be Enabled' instead!! Any ideas or should I just carry on and live with the default - after all makes no difference to how it works!

W

---

### Post by Forlong on 2008-06-24
Try running Compiz-Check on the Live CD -- what does it tell you?

---

