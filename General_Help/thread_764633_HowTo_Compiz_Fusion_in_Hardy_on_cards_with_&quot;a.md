---
title: "HowTo: Compiz Fusion in Hardy on cards with &quot;ati&quot;/&quot;radeon&quot; open source drivers"
date: 2008-04-24
forum: General Help
---

### Post by Rocket2DMn on 2008-04-24
Thank you for the [enlightening feedback]("http://ubuntuforums.org/showpost.php?p=4831424&postcount=46") on page 5, [COLOR="Sienna"]RAOF[/COLOR], we all appreciate this very much!

*[COLOR="Green"]Reason for this thread:[/COLOR]*
Older ATI cards have been blacklisted for Compiz Fusion because of a bug in the driver, but there is an easy workaround for many cards that use the open source ati drivers.  Radeon 9500 are the oldest cards to support the restricted "fglrx" drivers, so everything older requires the open source drivers to function properly.  A more technical explanation is offered in RAOF's post, linked above.

[COLOR="Red"]The appropriate method is as follows.[/COLOR]
Open a terminal and run:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

-> You may also need to install the Compiz settings manager program that you can access from System->Preferences->Advanced Desktop Effect Settings
```
sudo apt-get install compizconfig-settings-manager
```

You can now load Compiz Fusion and/or revert to Metacity (the basic window manager in Gnome) with the appropriate command:
```
compiz --replace &
metacity --replace &
```
I prefer making launchers in a panel for this, but it is not the only option.
-A program called "fusion-icon" is available in the repositories (accessed from Applications->System Tools->Compiz Fusion Icon).
-A simpler, cleaner, and equally effective tool is [compiz-switch]("http://forlong.blogage.de/article/pages/Compiz-Switch") by Forlong.  I suggest using the .deb installer file.

[COLOR="Blue"]**Remember that this is a workaround and may not work for everybody.**[/COLOR]  As RAOF also mentioned, do not be terribly surprised if this doesn't work or is somewhat unstable.  If you have further problems, you should consider running a forum search and then posting on one of the main support forums if you still need help.
For the record, my card is an ATI Mobility Radeon 9000.

---------------------------------------------------------
The original method suggested in this thread said to add SKIP_CHECKS="yes" to /usr/bin/compiz - while this works, it is not as solid as the updated method above (see [RAOF's post]("http://ubuntuforums.org/showpost.php?p=4831424&postcount=46")).

To fix this, simply open the launcher with the gksudo gedit code above and place a "#" symbol in front of the SKIP_CHECKS="yes" line that we added, save and close.
```
#SKIP_CHECKS="yes"
```
Alternatively, you can delete the line, though I don't usually suggest deleting from files as a precautionary measure (like if you get overzealous or just confused).

---------------------------------------------------------
*This guide also works on Intrepid Ibex Testing/Development release.*

---

### Post by say2sky on 2008-04-24
I have the same ATI Mobility Radeon 9000 on my Dell laptop. Now I run as your HowTo and have following output, what is the possible problem? Thanks for your help and HowTo.

```

say2sky@hardy:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (1024): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Fontconfig warning: no <cachedir> elements found. Check configuration.
Fontconfig warning: adding <cachedir>/var/cache/fontconfig</cachedir>
Fontconfig warning: adding <cachedir>~/.fontconfig</cachedir>
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Fontconfig warning: no <cachedir> elements found. Check configuration.
Fontconfig warning: adding <cachedir>/var/cache/fontconfig</cachedir>
Fontconfig warning: adding <cachedir>~/.fontconfig</cachedir>

```

---

### Post by Rocket2DMn on 2008-04-24
I'm not sure what those font problems are, but I don't think it is an issue, it seems like it may have created the correct stuff for you.  For the rest of the output, I got the same thing, I think this is just normal terminal output.
You should be able to use CF now.  You can setup 4 workspaces by right clicking the workspace switcher applet in the bottom panel and hitting Preferences.  4 workspaces is typical, though it started me with only 2.  You can then enable the cube and other desktop effects using compizconfig-settings-manager - note that it will prompt you to disable Desktop Wall if you enabled the Desktop Cube.

Again, I suggest making launchers in your panels to enable/disable compiz so you can avoid having to run these commands in terminal every time you want to change.
Right click the Panel area and hit Add to Panel, choose Custom Application Launcher and add the compiz/metacity commands from there.

---

### Post by say2sky on 2008-04-24
> **Rocket2DMn said:**
> I'm not sure what those font problems are, but I don't think it is an issue, it seems like it may have created the correct stuff for you.  For the rest of the output, I got the same thing, I think this is just normal terminal output.
You should be able to use CF now.  You can setup 4 workspaces by right clicking the workspace switcher applet in the bottom panel and hitting Preferences.  4 workspaces is typical, though it started me with only 2.  You can then enable the cube and other desktop effects using compizconfig-settings-manager - note that it will prompt you to disable Desktop Wall if you enabled the Desktop Cube.

Again, I suggest making launchers in your panels to enable/disable compiz so you can avoid having to run these commands in terminal every time you want to change.
Right click the Panel area and hit Add to Panel, choose Custom Application Launcher and add the compiz/metacity commands from there.

Thanks a lot for your help and now it works. I have set 4 workspaces and use Ctrl+Alt+arrow key to switch the 3D show. I am wonder if there is a way to show 3D with 6 faces and have other way to control the 3D cube rotating?

---

### Post by vexorian on 2008-04-24
hmnn Now that ATI got OS drivers I think I will move from nvidia this year when I get my new Desktop on Christmas time :)

---

### Post by Rocket2DMn on 2008-04-24
> **say2sky said:**
> Thanks a lot for your help and now it works. I have set 4 workspaces and use Ctrl+Alt+arrow key to switch the 3D show. I am wonder if there is a way to show 3D with 6 faces and have other way to control the 3D cube rotating?

Using the settings manager you can control keyboard shortcuts for the cube and other functions.  I think the cube works for any number of faces, it just isn't a cube at that point.


> **vexorian said:**
> hmnn Now that ATI got OS drivers I think I will move from nvidia this year when I get my new Desktop on Christmas time :)

ATI has had OS drivers for a long time, that is what older ATI cards have to use.  The proprietary fglrx drivers are suggested for the newer ATI cards.  Long story short, you will be using proprietary drivers on newer nvidia or ati cards, but they tend to work OK.  The OS ati drivers are nothing to be proud of, they just keep those of us with older cards in the game.

---

### Post by Uikku on 2008-04-25
Thanks a lot. Adding **SKIP_CHECKS="yes"** to **/usr/bin/compiz** did the trick. Now the visual effects can be set on normally, that is via Settings menu.

I'm using an old Acer Aspire 2001 with ATI Mobility Radeon 9200.

---

### Post by say2sky on 2008-04-25
to Rocket2DMn:

I have another question about 3D desktop on ubuntu. I think you know a lot in 3D desktop field and use same ATI Mobility Radeon 9000 so ask this question which is not very ralated with Compiz Fusion. If you  don't want to answer just ignore it. :)

In the past I also try Beryl on my laptop but it also doesn't work. Now if there are a similar and simple solution just like you provide in this HowTo which can let  Beryl run on  ATI Mobility Radeon 9000. Thank you very much.

updated:
haha I googled and found it was a stupid question. Now Beryl already merged with Compiz and is named new name Compiz Fusion. Am I right? Thanks! :guitar:

---

### Post by Rocket2DMn on 2008-04-25
> **say2sky said:**
> to Rocket2DMn:

I have another question about 3D desktop on ubuntu. I think you know a lot in 3D desktop field and use same ATI Mobility Radeon 9000 so ask this question which is not very ralated with Compiz Fusion. If you  don't want to answer just ignore it. :)

In the past I also try Beryl on my laptop but it also doesn't work. Now if there are a similar and simple solution just like you provide in this HowTo which can let  Beryl run on  ATI Mobility Radeon 9000. Thank you very much.

Compiz Fusion replaced Beryl last year, CF is the spawn of Beryl and Compiz, so unless you are using a much older version of Ubuntu, CF is what you are looking for.  Back in Feisty (a year ago), I installed Beryl using this guide: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
However, if you are up to date with Ubuntu, you do not need this.  Gutsy and Hardy both use Compiz Fusion in place of the outdated Beryl.
Our cards do not support the proprietary fglrx drivers, so it's important that you get rid of those if you have them.  Hardy autodetects our card decently, unlike in past released when we had to reconfigure X.

---

### Post by say2sky on 2008-04-25
> **Rocket2DMn said:**
> Compiz Fusion replaced Beryl last year, CF is the spawn of Beryl and Compiz, so unless you are using a much older version of Ubuntu, CF is what you are looking for.  Back in Feisty (a year ago), I installed Beryl using this guide: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
However, if you are up to date with Ubuntu, you do not need this.  Gutsy and Hardy both use Compiz Fusion in place of the outdated Beryl.
Our cards do not support the proprietary fglrx drivers, so it's important that you get rid of those if you have them.  Hardy autodetects our card decently, unlike in past released when we had to reconfigure X.

You are right and now I know the transition background and it work very well on my laptop with no lag. :)

---

### Post by Rocket2DMn on 2008-04-25
> **say2sky said:**
> You are right and now I know the transition background and it work very well on my laptop with no lag. :)

groovy!

---

### Post by lasombra on 2008-04-25
Well my card is not on the blacklist, but compiz was not working:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)


Now after SKIP_CHECKES=yes added, I can use the desktop effects again.

---

### Post by drkjstr on 2008-04-26
Had to do a clean instally of Hardy (for other reasons) and did the setup form the first post, and it worked like a charm. Thanks!

---

### Post by edu77pose on 2008-04-26
Thanks for the tip, straight forward & it worked :)

I tried it on my gf's notebook toshiba tecra A1 and it brought compiz-fusion and awn back to life.

Much appreciated.

---

### Post by neyuru on 2008-04-27
Thanks for the workaround. I entered the command compiz --replace and got this:

yorcho@yorcho-laptop:~$ gksudo gedit /usr/bin/compiz
yorcho@yorcho-laptop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
yorcho@yorcho-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (1024): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

What does this mean? How can I quit the terminal?

---

### Post by neyuru on 2008-04-27
P.S. The visual effects did work correctly for me. I have a Radeon Mobility 7500 C. I had to do this in Hardy but in Gutsy there was no necessity for this.

---

### Post by neyuru on 2008-04-27
> **neyuru said:**
> P.S. The visual effects did work correctly for me. I have a Radeon Mobility 7500 C. I had to do this in Hardy but in Gutsy there was no necessity for this.

Never mind the previous two messages. How do I enable the cube?

thanks

---

### Post by Rocket2DMn on 2008-04-27
> **neyuru said:**
> Never mind the previous two messages. How do I enable the cube?

thanks

You need to install compizconfig-settings-manager
```
sudo apt-get install compizconfig-settings-manager
```
Then go to System->Preferences->Advanced Desktop Effects Settings and check the box for Desktop Cube and allow it to disabled Desktop Wall.

---

### Post by knight666 on 2008-04-27
Hi,

Thanks for the advice in this thread, it really helped me out. :)
But I still have an annoying problem: I'm running Ubuntu 8.04 with all the latest updates on a Compaq Evo N610c (1.8 Ghz Mobile Pentium 4, 512 MB RAM, ATI Radeon Mobility 7500 32 MB), and with some haxxing (manually installing xserver-xgl, changing xorg.conf, etc) I got Compiz working.
But, not entirely.
Scrolling is very slow in windows and even though glxgears says I have an fps of 35-45 (under Compiz) and 75-80 (under Metacity), the window looks extremely choppy.

When I open a menu under Compiz, there is a white bar next to the end of the alpha blend shadow.

Finally, this is the output of compiz:
```
Checking for Xgl: present.
Checking for nVidia: not present.
Checkign for Xgl: present.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove the value so that operation can continue properly.
```
The option is set to its default value, "[]".

Help? <:(

---

### Post by hodenkat on 2008-04-27
Dude! YOU RULE!:guitar:

On first boot after making changes I was able to enable effects and they work smoothly just like they were on 7.10! AWSOME!

Thank you!

Running 8.04 on an IBM T-40 laptop : ATI Radeon Mobility 7500

---

### Post by Rocket2DMn on 2008-04-27
> **knight666 said:**
> Hi,

Thanks for the advice in this thread, it really helped me out. :)
But I still have an annoying problem: I'm running Ubuntu 8.04 with all the latest updates on a Compaq Evo N610c (1.8 Ghz Mobile Pentium 4, 512 MB RAM, ATI Radeon Mobility 7500 32 MB), and with some haxxing (manually installing xserver-xgl, changing xorg.conf, etc) I got Compiz working.
But, not entirely.
Scrolling is very slow in windows and even though glxgears says I have an fps of 35-45 (under Compiz) and 75-80 (under Metacity), the window looks extremely choppy.

When I open a menu under Compiz, there is a white bar next to the end of the alpha blend shadow.

Finally, this is the output of compiz:
```
Checking for Xgl: present.
Checking for nVidia: not present.
Checkign for Xgl: present.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove the value so that operation can continue properly.
```
The option is set to its default value, "[]".

Help? <:(

OK, let's first uninstall xserver-xgl, I don't think you want that (I don't have it and I don't run laggy).  Other people have complained in other threads about lag on all different types of cards and I'm tempted to say its because of xserver-xgl, so you're gonna test that out for me :)  It can always be reinstalled of course.  Please post the output of all of these commands exactly as they appear in your terminal.
```
metacity --replace
sudo apt-get remove --purge xserver-xgl
cat ~/.gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge
compiz --replace
```

---

### Post by BoardStupid on 2008-04-27
I've followed this tutorial (and others) but I still cant "extra" visual effects enabled. I think I'm on the brink of cracking it, but I can't quite figure it out.

My output from compiz --replace is
```
mark@laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5975 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/local/bin/compiz: 409: /usr/local/bin/compiz.real: not found

```

Rocket2DMn really seems to know what s/he's on about so I'm hoping I can be helped like the rest of the people in this thread. I miss my desktop effects :(

My GFX card is an ATI Radeon Xpress 1100. [This is the laptop I'm using]("http://www.ciao.co.uk/Acer_Aspire_5051AWXMi_Turion_64_mobile_technology_MK_36_2_GHz_14_1_TFT__6594350#productdetail")

---

### Post by Rocket2DMn on 2008-04-27
> **BoardStupid said:**
> I've followed this tutorial (and others) but I still cant "extra" visual effects enabled. I think I'm on the brink of cracking it, but I can't quite figure it out.

My output from compiz --replace is
```
mark@laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5975 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/local/bin/compiz: 409: /usr/local/bin/compiz.real: not found

```

Rocket2DMn really seems to know what s/he's on about so I'm hoping I can be helped like the rest of the people in this thread. I miss my desktop effects :(

My GFX card is an ATI Radeon Xpress 1100. [This is the laptop I'm using]("http://www.ciao.co.uk/Acer_Aspire_5051AWXMi_Turion_64_mobile_technology_MK_36_2_GHz_14_1_TFT__6594350#productdetail")

Can you please post the output of the following commands:
```
lspci | grep VGA
cat /etc/X11/xorg.conf
```

---

### Post by b3y0nd on 2008-04-27
I followed the instructions above but got this error message:

beyond@beyond-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:02.0 0300: 1002:5960 (rev 01) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

I have a ATI Radeon 9200

---

### Post by Rocket2DMn on 2008-04-27
> **b3y0nd said:**
> I followed the instructions above but got this error message:

beyond@beyond-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:02.0 0300: 1002:5960 (rev 01) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

I have a ATI Radeon 9200

I've seen this a few times, but people haven't gotten back to me.  I need to see the output of
```
cat ~/.gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge
```

---

### Post by BoardStupid on 2008-04-27
Thanks for the super quick reply.
```
mark@laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
```
And:
```
mark@laptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
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
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"	"true"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Driver		"fglrx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
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

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

```

Could you give a quick brief of what you're looking for so I know why I'm doing this if it happens again? Thanks again for the help

---

### Post by BoardStupid on 2008-04-27
double post. Sorry :s

---

### Post by Rocket2DMn on 2008-04-27
> **BoardStupid said:**
> Thanks for the super quick reply.
```
mark@laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
```
And:
```
mark@laptop:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
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
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"	"true"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Driver		"fglrx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
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

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

```

Could you give a quick brief of what you're looking for so I know why I'm doing this if it happens again? Thanks again for the help

OK, it shows that you are using the restricted fglrx drivers for your card.  Did you set these up yourself?  A brief google search shows that this card probably should be using the fglrx drivers rather than the open source ones (which this thread is about, but that's ok).  You should try using EnvyNG to download the correct restricted drivers for your card.  You can follow directions here - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

Earlier you said "/usr/local/bin/compiz: 409: /usr/local/bin/compiz.real: not found" as part of the compiz --replace output, which is strange because that is not where compiz is supposed to be.  Hopefully installing the correct video drivers with EnvyNG will get you going, otherwise you may need to reinstall compiz itself.

---

### Post by BoardStupid on 2008-04-27
I already had Envy installed but read that I had to completely remove end install EnvyNG for Hardy, so I went ahead and did that. I then used EnvyNG to automatically install the ATI driver. 
I then saw in another post that Compiz and all it's components must be completley removed and re-installed so I did that also. 

I will try uninstalling Compiz and my driver again and reinstalling everything again to see if that makes any difference. Is it worth uninstalling other things such as AWN and Screenlets too, as these both rely on advance desktop settings being active?

---

### Post by Rocket2DMn on 2008-04-27
Don't bother with the other stuff, just Compiz and video drivers.

---

### Post by BoardStupid on 2008-04-27
I'm afraid that didn't help. Still no fancy effects.
I wonder why it's not working as both installations went without a hitch. I guess I'll have to work on it a bit more. Thanks for your help anyway.
I came across a thread which I missed before, and compiz is working now. it's [http://ubuntuforums.org/showthread.php?t=766212]("http://ubuntuforums.org/showthread.php?t=766212") in case anybody comes here with the same problem as I did.

---

### Post by neyuru on 2008-04-27
Maybe some of you might find this usefull:

If you want to get the cube, and if you get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: **Couldn't find package compizconfig-settings-manager**

when using this command:

**sudo apt-get install compizconfig-settings-manager**

you might want to run:

**sudo aptitude update**

THIS WILL INSTALL SOME PACKAGES SO THAT YOU CAN USE THE CUBE!

enjoy... and thanks to Rocket2DMn

---

### Post by krugger on 2008-04-28
Adding the SKIP_CHECKS="yes" did work for me, still I wanted to give some feedback. I have a ATI Radeon Mobility M6 and use the ati driver which is white listed.

From glxinfo I know that:

direct rendering: Yes
server glx extensions: ... GLX_EXT_texture_from_pixmap, ...

But running compiz --replace will fail the texture_from_pixmap extension test. 

Checking for texture_from_pixmap: not present.

Then it will failover to indirect rendering:

Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (1024): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

This happens because the check is done with:

if [ $(glxinfo | grep GLX_EXT_texture_from_pixmap -c ) -gt 2 ]; ...

So maybe the glxinfo part has changed and the compiz people did not update their script for the new 1.4 Xserver. 

There is also a small problem with gconf:
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

This seems to be because ./gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge does not exist, but is mentioned in ./gconf/apps/compiz/plugins/scale/allscreens/options/%gconf.xml

content of %gconf.xml:
<?xml version="1.0"?>
<gconf>
        <entry name="initiate_edge" mtime="1193157882" type="list" ltype="string">
        </entry>
        <entry name="initiate_bell" mtime="1193157882" type="bool" value="false">
        </entry>
</gconf>

so it doesn't like to have empty list of strings. Don't know what to put in it, so suggestions are welcome.

---

### Post by Rocket2DMn on 2008-04-28
Yeah, seems a little buggy sometimes, I have seen people with the pixmap and initiate_edge problem.  However, as long as it works, it should be OK.  I had one user reinstall compiz and that fixed the initiate edge problem for him/her (since compiz wouldn't even load), but for another user, it failed, so who knows.  I will keep looking into these problems.

---

### Post by neyuru on 2008-04-28
> **krugger said:**
> Adding the SKIP_CHECKS="yes" did work for me, still I wanted to give some feedback. I have a ATI Radeon Mobility M6 and use the ati driver which is white listed.

From glxinfo I know that:

direct rendering: Yes
server glx extensions: ... GLX_EXT_texture_from_pixmap, ...

But running compiz --replace will fail the texture_from_pixmap extension test. 

Checking for texture_from_pixmap: not present.

Then it will failover to indirect rendering:

Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (1024): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

This happens because the check is done with:

if [ $(glxinfo | grep GLX_EXT_texture_from_pixmap -c ) -gt 2 ]; ...

So maybe the glxinfo part has changed and the compiz people did not update their script for the new 1.4 Xserver. 

There is also a small problem with gconf:
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

This seems to be because ./gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge does not exist, but is mentioned in ./gconf/apps/compiz/plugins/scale/allscreens/options/%gconf.xml

content of %gconf.xml:
<?xml version="1.0"?>
<gconf>
        <entry name="initiate_edge" mtime="1193157882" type="list" ltype="string">
        </entry>
        <entry name="initiate_bell" mtime="1193157882" type="bool" value="false">
        </entry>
</gconf>

so it doesn't like to have empty list of strings. Don't know what to put in it, so suggestions are welcome.

Maybe you should report this to the people making compiz

---

### Post by Rocket2DMn on 2008-04-28
> **neyuru said:**
> Maybe you should report this to the people making compiz

They are not likely to help since they don't support the open source ati driver.  Remember, we are using a workaround.  With any luck though, you might be able to get a developer to at least look at it.

---

### Post by dr.phees on 2008-04-28
Thanks! The solution with SKIP_CHECKS="yes" worked for me. I'm using xubuntu, compiz worked flawless with 7.10 and now again in 8.04.

I don't actually understand why my card is forbidden to run compiz by default. I think a bit more verbose output from compiz would make sense, until now I thought it was my driver or xserver setup. To the developers: JUST TELL IT'S TURNED OFF FOR THE INSTALLED GRAPHICS CARD! That would have saved about two hours on my account. Well, now I could have wobbly windows again, if I'd like to. ;)

Otherwise: Thanks to all who made 8.04 possible!

---

### Post by splicer on 2008-04-28
I don't know if this helps anyone or not, but as I was trouble-shooting getting compiz to work (along with resolving the "Desktop effects could not be enabled" when switching from None to Normal effects), I discovered I had two sets of kernel modules installed:

  linux-restricted-modules-2.6.24-16-generic

and 

  linux-restricted-modules-2.6.22-*-generic

Both of which had ati drivers.  I removed the 2.6.22 restricted modules (which were probably for Gutsy) and rebooted.  Everything appears to work again, I can toggle effects off/on and all my compiz stuff seems to be working again.

This worked for me ... your mileage may vary.

---

### Post by rekster on 2008-04-28
Have problems as well, please pardon me if I misread or missed something said earlier in these posts, I did read them.

Running Ubuntu 8.04 on Acer Ferrari 4000 notebook that has ATI X700.
I enabled the ATI accelerated graphics driver as well which seemed to work well as 3d gaming is great (not sure if this has anything to do with compiz though lol)

This is the console log:

$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5653 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.



Any suggestions?

---

### Post by Rocket2DMn on 2008-04-28
> **splicer said:**
> I don't know if this helps anyone or not, but as I was trouble-shooting getting compiz to work (along with resolving the "Desktop effects could not be enabled" when switching from None to Normal effects), I discovered I had two sets of kernel modules installed:

  linux-restricted-modules-2.6.24-16-generic

and 

  linux-restricted-modules-2.6.22-*-generic

Both of which had ati drivers.  I removed the 2.6.22 restricted modules (which were probably for Gutsy) and rebooted.  Everything appears to work again, I can toggle effects off/on and all my compiz stuff seems to be working again.

This worked for me ... your mileage may vary.

Thank you for the feedback, that sounds like it could be useful for others having trouble after a dist upgrade.  If you have any other threads in which that method has worked for people, please let me know and I will add it to the original post as a troubleshooting method (assuming it's a solid solution).
Commands would probably be something like
```
sudo apt-get remove linux-restricted-modules-*
sudo apt-get autoremove
sudo apt-get install linux-restricted-modules-`uname -r`
```

---

### Post by Rocket2DMn on 2008-04-28
> **rekster said:**
> Have problems as well, please pardon me if I misread or missed something said earlier in these posts, I did read them.

Running Ubuntu 8.04 on Acer Ferrari 4000 notebook that has ATI X700.
I enabled the ATI accelerated graphics driver as well which seemed to work well as 3d gaming is great (not sure if this has anything to do with compiz though lol)

This is the console log:

$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5653 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.



Any suggestions?

With your card, you need the restricted ati drivers called fglrx - is that what you are saying you installed?  If not, check out EnvyNG - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
If the problem persists, you may want to reinstall compiz
```
sudo apt-get remove --purge compiz
sudo apt-get install compiz
```
If that doesn't work, you should start a new thread to get help with that since this HowTo is for open source ati drivers which you can't use on your card.

---

### Post by rekster on 2008-04-28
Ok, you are right I am using the restricted drivers, not the open source ones.  I guess I'll search around some more or maybe start a new forum topic then, sorry for the misunderstanding.  One good note is, I'm happy to have found out about EnvyNG in any case however compiz still is not functional.  Maybe one of these years I'll get it working (had no luck on prior versions of ubuntu either) lol.

Cheers.


EDIT:  Sorry for the bother, I got it resolved I guess the darn thing was working afterall, I just didnt have 'rotate' cube enabled and I didn't understand how it worked.  Thanks again for the help.

---

### Post by neyuru on 2008-04-28
> **Rocket2DMn said:**
> They are not likely to help since they don't support the open source ati driver.  Remember, we are using a workaround.  With any luck though, you might be able to get a developer to at least look at it.

:(

---

### Post by Rocket2DMn on 2008-04-28
> **neyuru said:**
> :(

Please don't take that too negatively, I do suggest talking to the developers if you can, it is how things get done.  Although I don't imagine they are planning on supporting our drivers, we can always try.  I suppose if enough people push them, they can at least put some functionality in to enable it after you click a Yes button saying you understand that the drivers are not officially supported.
I will try and remember to look around later to see if I can find who to complain to or where to do it.  I may even offer my coding and testing services.

---

### Post by neyuru on 2008-04-28
> **Rocket2DMn said:**
> Please don't take that too negatively, I do suggest talking to the developers if you can, it is how things get done.  Although I don't imagine they are planning on supporting our drivers, we can always try.  I suppose if enough people push them, they can at least put some functionality in to enable it after you click a Yes button saying you understand that the drivers are not officially supported.
I will try and remember to look around later to see if I can find who to complain to or where to do it.  I may even offer my coding and testing services.

Nice! whenever you need support (raising hands, crowd, etc) count on us.

---

### Post by RAOF on 2008-04-29
Firstly, everyone has probably noticed the sticky below this one, but just to reiterate: your cards were blacklisted because things were either unstable or didn't work.  Don't be terribly surprised if you find this to be the case after skipping the checks :).

Secondly, editing /usr/bin/compiz is fragile; your edits will be lost if and when compiz is updated.  The other sticky describes a better way - namely, to add SKIP_CHECKS=1 to your user's configuration with
```

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

```

> **krugger said:**
> ...
direct rendering: Yes
server glx extensions: ... GLX_EXT_texture_from_pixmap, ...

But running compiz --replace will fail the texture_from_pixmap extension test. 

Checking for texture_from_pixmap: not present.

Then it will failover to indirect rendering:

Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (1024): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
...

This is because your drivers don't support GL_EXT_texture_from_pixmap in a direct rendering context, which is basically a limitation of the current DRI infrastructure, give or take.  I think nvidia are basically the only drivers which do this (and possibly some git Intel drivers, with git libdrm and git Xorg, I'm not quite sure how far along this is ;)) at the moment.

---

### Post by toobitz on 2008-04-29
Thanks a lot for this thread and your effort! I hope I'm not being inpolite by pasting my problem here, but since I upgraded my laptop from Gutsy to Hardy I've been desperately trying to get Compiz to work again with, well let's say, limited success.

I've got a Thinkpad T43p with the following video card:
```
01:00.0 VGA compatible controller: ATI Technologies Inc M24GL [Mobility FireGL V3200] (rev 80)
```

I was using the Open Source "ati" driver before upgrading (I had no problems whatsoever using Compiz) and I acutally would like to continue to do so, but when I try to start compiz after upgrading in a terminal with compiz --replace &, I get:
```
Checking for Xgl: not present.
Found laptop using ati driver.
Found laptop using radeon driver.
Detected PCI ID for VGA: 01:00.0 0300: 1002:3154 (rev 80) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "switch_windows"
```

Xorg.0.log is here: [http://ubuntuusers.de/paste/204459/](http://ubuntuusers.de/paste/204459/)
the output of glxinfo is here: [http://ubuntuusers.de/paste/204461/](http://ubuntuusers.de/paste/204461/)
here's my xorg.conf: [http://ubuntuusers.de/paste/204463/](http://ubuntuusers.de/paste/204463/) 

...and here's the output of "LIBGL_DEBUG=verbose glxinfo":
```
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 5.3.0 r300 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r300_dri.so
libGL error: dlopen /usr/lib/dri/r300_dri.so failed (/usr/lib/dri/r300_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: r300_dri.so
libGL: XF86DRIGetClientDriverName: 5.3.0 r300 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r300_dri.so
libGL error: dlopen /usr/lib/dri/r300_dri.so failed (/usr/lib/dri/r300_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: r300_dri.so
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x58 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
```

Of course I also tried to use the fglrx driver, tried both methods (using the driver/package provided by Ubuntu and tried building the driver by myself). None of these methods worked, when using the self built driver, I get a segmentation fault when entering "fglrxinfo", "glxinfo", "glxgears" in a terminal or if I try to start compiz. This also happens when I install the whole thing using envy-ng.

I just don't get it why my previous configuration won't work anymore! But what's really strange is the following: when I enter the following
```
sudo compiz --replace &
```
then compiz will actually start and emerald too, with the following output:
```
Checking for Xgl: not present.
Found laptop using ati driver.
Found laptop using radeon driver.
Detected PCI ID for VGA: 01:00.0 0300: 1002:3154 (rev 80) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Couldn't find a perfect decorator match; trying all decorators
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

What's going on here? Anyone has a hint because I'm at a complete loss now...

---

### Post by Rocket2DMn on 2008-04-29
> **RAOF said:**
> Firstly, everyone has probably noticed the sticky below this one, but just to reiterate: your cards were blacklisted because things were either unstable or didn't work.  Don't be terribly surprised if you find this to be the case after skipping the checks :).

Secondly, editing /usr/bin/compiz is fragile; your edits will be lost if and when compiz is updated.  The other sticky describes a better way - namely, to add SKIP_CHECKS=1 to your user's configuration with
```

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

```



This is because your drivers don't support GL_EXT_texture_from_pixmap in a direct rendering context, which is basically a limitation of the current DRI infrastructure, give or take.  I think nvidia are basically the only drivers which do this (and possibly some git Intel drivers, with git libdrm and git Xorg, I'm not quite sure how far along this is ;)) at the moment.

Thank you RAOF, I will update the original post right away.  This is exactly the type of feedback I had been hoping for.

---

### Post by neyuru on 2008-04-29
Some reference to restricted drivers, other to open source drivers. How do I know which one is my system using? Which one is better? Has anyone tried installing drivers with Wine? (for example those found in Dell's system drivers?)

---

### Post by RAOF on 2008-04-29
> **toobitz said:**
> ...
Xorg.0.log is here: [http://ubuntuusers.de/paste/204459/](http://ubuntuusers.de/paste/204459/)
the output of glxinfo is here: [http://ubuntuusers.de/paste/204461/](http://ubuntuusers.de/paste/204461/)
here's my xorg.conf: [http://ubuntuusers.de/paste/204463/](http://ubuntuusers.de/paste/204463/) 

...and here's the output of "LIBGL_DEBUG=verbose glxinfo":
```
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 5.3.0 r300 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r300_dri.so
libGL error: dlopen /usr/lib/dri/r300_dri.so failed (/usr/lib/dri/r300_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: r300_dri.so
libGL: XF86DRIGetClientDriverName: 5.3.0 r300 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/r300_dri.so
libGL error: dlopen /usr/lib/dri/r300_dri.so failed (/usr/lib/dri/r300_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: r300_dri.so
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x58 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
```

...

I just don't get it why my previous configuration won't work anymore! But what's really strange is the following: when I enter the following
```
sudo compiz --replace &
```
then compiz will actually start and emerald too, with the following output:
```
Checking for Xgl: not present.
Found laptop using ati driver.
Found laptop using radeon driver.
Detected PCI ID for VGA: 01:00.0 0300: 1002:3154 (rev 80) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Couldn't find a perfect decorator match; trying all decorators
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

What's going on here? Anyone has a hint because I'm at a complete loss now...

That's very weird.  If it didn't work using *sudo* I'd suggest reinstalling the 3D stack with
```

sudo aptitude reinstall ~nmesa

```
which would reinstall any package with 'mesa' in the name.  It might still be worth a try, but I'm not confident.  Do you have any strange environment variables lying around?  Have you previously tried building mesa from source and possibly have some remnants lying around?  Does either of 'echo $LD_PRELOAD' or 'echo $LD_LIBRARY_PATH' give any output?

Oh, finally?  "It didn't work as my user so I tried running it as root" isn't a particularly good debugging style :).  In some cases doing this will break running the software as not-root in the future.

> **neyuru said:**
> Some reference to restricted drivers, other to open source drivers. How do I know which one is my system using? Which one is better? Has anyone tried installing drivers with Wine? (for example those found in Dell's system drivers?)

System->Administration->Hardware Drivers gives you a list of all the hardware in your system for which a restricted driver exists, whether you're using it, and a button to press to enable it.  I'd suggest using free drivers whenever possible - they're generally less awkward, and we're able to support them.  If you have problems with 3D you can try enabling the restricted driver and this may help (or may not).

You can't install drivers in Wine.  Wine doesn't talk directly to the hardware at all, and doesn't actually implement the Windows kernel (mostly), so there are none of the hooks that drivers would need.  Also, that wouldn't be useful for your linux system since they'd only run in wine ;).

---

### Post by Rocket2DMn on 2008-04-29
Just an FYI, this thread was unstickied and linked from this sticky on the General Help forum: [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by neyuru on 2008-04-29
[QUOTE=RAOF]

System->Administration->Hardware Drivers gives you a list of all the hardware in your system for which a restricted driver exists, whether you're using it, and a button to press to enable it.  I'd suggest using free drivers whenever possible - they're generally less awkward, and we're able to support them.  If you have problems with 3D you can try enabling the restricted driver and this may help (or may not).

You can't install drivers in Wine.  Wine doesn't talk directly to the hardware at all, and doesn't actually implement the Windows kernel (mostly), so there are none of the hooks that drivers would need.  Also, that wouldn't be useful for your linux system since they'd only run in wine ;).[/QUOTE]


ohh.. that's nice to know

---

### Post by Goombie on 2008-04-29
I just wanted to say that this method worked for me, too. I admit, I only did it a couple minutes ago, but so far everything is good. :) If I remember, I'll post if anything is broken. :popcorn:

---

### Post by john91 on 2008-04-30
Hmm... this hasn't worked for me.  

Here's the output of 'compiz --replace':
```
mcleanj@mcleanj:~$ mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
mcleanj@mcleanj:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

Any ideas would be helpful.  compiz isn't neccessary for me, but it is nice.

---

### Post by Rocket2DMn on 2008-04-30
> **john91 said:**
> Hmm... this hasn't worked for me.  

Here's the output of 'compiz --replace':
```
mcleanj@mcleanj:~$ mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
mcleanj@mcleanj:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

Any ideas would be helpful.  compiz isn't neccessary for me, but it is nice.

Did you upgrade to Hardy or did you do a fresh install?
First try reconfiguring X
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Now restart X with CTRL+ALT+BACKSPACE

If it still doesn't work, you may want to try reinstalling compiz
```
sudo apt-get remove --purge compiz
sudo apt-get install compiz
```

---

### Post by toobitz on 2008-04-30
Thanks for your reply, really appreciate it!

> **RAOF said:**
> That's very weird.  If it didn't work using *sudo* I'd suggest reinstalling the 3D stack with
```

sudo aptitude reinstall ~nmesa

```
which would reinstall any package with 'mesa' in the name.  It might still be worth a try, but I'm not confident.

I just did that but it did not help.

> **RAOF said:**
> Do you have any strange environment variables lying around?

Not as far as I can see, except for $LIBGL_DRIVERS which is "/usr/lib/dri"

> **RAOF said:**
> Have you previously tried building mesa from source and possibly have some remnants lying around?

No, I've never tried building mesa by myself.

> **RAOF said:**
> Does either of 'echo $LD_PRELOAD' or 'echo $LD_LIBRARY_PATH' give any output?

Yes, $LD_LIBRARY_PATH is "/usr/lib/xorg", $LD_PRELOAD is empty.

> **RAOF said:**
> Oh, finally?  "It didn't work as my user so I tried running it as root" isn't a particularly good debugging style :).  In some cases doing this will break running the software as not-root in the future.

Yes, of course you're right, I know that and normally don't do this but I read in another thread that a guy tried it "successfully" and I just wanted to check. Also, this means basically my environment is able to run 3D applications, just as normal user I'm not. Of course I already tried moving ~/.compizconfig and ~/.emerald out of the way but that wasn't it.

---

### Post by john91 on 2008-04-30
reconfiguring and restarting the X server didn't work, and neither did reinstalling compiz.

EDIT: nevermind, I've got it working great now!

---

### Post by toobitz on 2008-04-30
> **toobitz said:**
> Yes, $LD_LIBRARY_PATH is "/usr/lib/xorg", $LD_PRELOAD is empty.

A follow-up to my own post, I had an idea just after writing it: since compiz was working when started as root and not if started as ordinary user, it must have something do to with my environment (variables). And voilà, I unset LD_LIBRARY_PATH and now compiz starts like a charm.

Now there's my next problem: where is this LD_LIBRARY_PATH being set? I just tried and added another user to the system - and this users has LD_LIBRARY_PATH set to /usr/lib/xorg just like me, so this must be something system-wide.. /etc/bash.bashrc does not contain it and putting "unset LD_LIBRARY_PATH" into ~/.bashrc doesn't do the trick either.. do you have any idea where this variable is being set?

Thanks a lot for your help already RAOF, you put me into the right direction!

---

### Post by bronsoja on 2008-05-01
I followed the steps in the first post to add in the skip checks, and I still wasn't getting compiz running.  I eventually figured out that my xorg.conf wasn't configured at all.

this is my video card:  ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)

My xorg.conf was this [http://ubuntuusers.de/paste/209267/](http://ubuntuusers.de/paste/209267/)

I figured out I needed to change "vesa" to "ati".  After doing that and reloading x, (and having already put the skip text in), compiz was working.  

Since it looks like my xorg.conf wasn't configured beyond default initially, i was trying to get it set up correctly. I haven't had the best luck searching around and I was hoping you guys could point me somewhere to figure out what settings I need to have in there for best performance, or if there is some util to help me do that.  I'm also going to eventually be trying to get my second monitor working hopefully, so any tips in that area are appreciated.  

thanks for the help

---

### Post by Rocket2DMn on 2008-05-01
> **bronsoja said:**
> I followed the steps in the first post to add in the skip checks, and I still wasn't getting compiz running.  I eventually figured out that my xorg.conf wasn't configured at all.

this is my video card:  ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)

My xorg.conf was this [http://ubuntuusers.de/paste/209267/](http://ubuntuusers.de/paste/209267/)

I figured out I needed to change "vesa" to "ati".  After doing that and reloading x, (and having already put the skip text in), compiz was working.  

Since it looks like my xorg.conf wasn't configured beyond default initially, i was trying to get it set up correctly. I haven't had the best luck searching around and I was hoping you guys could point me somewhere to figure out what settings I need to have in there for best performance, or if there is some util to help me do that.  I'm also going to eventually be trying to get my second monitor working hopefully, so any tips in that area are appreciated.  

thanks for the help

The new version of X seems to rely more on autodetection than xorg.conf, and to be honest, it has made it a pain in the butt to configure X for cards that aren't autodetected.  However, you should be able to use the default xorg.conf (works for me on the same card).  If you run
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
then restart X with CTRL+ALT+BACKSPACE, xorg.conf will reset itself to the autodetected defaults for your system.  At this point, you should be able to use compiz since you added the SKIP_CHECKS.

---

### Post by bronsoja on 2008-05-01
Yeah, whenever I do the reconfigure to generate xorg.conf according to the autodetection, i get one like i linked in my first post, where it doesn't even have the Driver set "ati".  

Is it possible the autodetection is not working correctly since my card is listed as "Mobility FireGL 9000" rather than "Mobility Radeon 9000"?

---

### Post by bronsoja on 2008-05-01
**double posted

---

### Post by Rocket2DMn on 2008-05-01
The autodetection won't show a driver, just the "Configured Video Device" stuff.  Is it autogenerating to say vesa?
Can you please post the output of
```
compiz --replace
```

---

### Post by The_Seeker on 2008-05-01
Hi Rocket,

Thanks for all the help. I followed your instructions and have got compiz to work :)

But, when i do enable compiz, scrolling in firefox is really slow. Have you experienced this?

---

### Post by Rocket2DMn on 2008-05-01
> **The_Seeker said:**
> Hi Rocket,

Thanks for all the help. I followed your instructions and have got compiz to work :)

But, when i do enable compiz, scrolling in firefox is really slow. Have you experienced this?

No, what exact video card do you have?  You can post
```
lspci | grep VGA
```
Also, if you have xserver-xgl installed, you may need to uninstall that.  If for some reason that causes problems, it can easily be reinstalled, though I don't think it is installed by default and indeed should NOT be needed or wanted
```
sudo apt-get remove xserver-xgl
```

---

### Post by The_Seeker on 2008-05-01
> **Rocket2DMn said:**
> No, what exact video card do you have?  You can post
```
lspci | grep VGA
```
Also, if you have xserver-xgl installed, you may need to uninstall that.  If for some reason that causes problems, it can easily be reinstalled, though I don't think it is installed by default and indeed should NOT be needed or wanted
```
sudo apt-get remove xserver-xgl
```

Thanks for the quick reply,Rocket.
The video card that I am using is :

```

 lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

```

and xserver -xgl is not installed.

---

### Post by Rocket2DMn on 2008-05-01
> **The_Seeker said:**
> Thanks for the quick reply,Rocket.
The video card that I am using is :

```

 lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

```

and xserver -xgl is not installed.

I have noticed other people having problems with this card.  Why don't you try uninstalling then reinstalling compiz:
```
sudo apt-get remove --purge compiz
sudo apt-get install compiz
```
Then post here the output of
```
cat /etc/X11/xorg.conf
compiz --replace
```

---

### Post by The_Seeker on 2008-05-01
> **Rocket2DMn said:**
> I have noticed other people having problems with this card.  Why don't you try uninstalling then reinstalling compiz:
```
sudo apt-get remove --purge compiz
sudo apt-get install compiz
```
Then post here the output of
```
cat /etc/X11/xorg.conf
compiz --replace
```

i tried uninstalling and re-installing compiz. But sadly, the issue still persists. :(

Below is the xorg.conf file 

```

# xorg.conf (X.Org X Window System server configuration file)
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
	Boardname	"ATI Radeon (vesa)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1280x1024"
	Horizsync	31.5-81.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1600x1200@65"	"1152x864@75"	"1600x1200@60"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #     
	Identifier	"device1"
	Boardname	"ATI Radeon (vesa)"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	1
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" #     
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #     
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

When i do enable compiz, i get all the eye-candy but the scroll in firefox is miserably slow.

---

### Post by Rocket2DMn on 2008-05-01
Did you upgrade from Gutsy?  The new X doesn't like xorg.conf as much as it used to, so you should try reconfigured X to get a more generic xorg.conf and let X do its new autodetection thing at runtime:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
then restart X with CTRL+ALT+BACKSPACE

---

### Post by bronsoja on 2008-05-01
> **Rocket2DMn said:**
> The autodetection won't show a driver, just the "Configured Video Device" stuff.  Is it autogenerating to say vesa?
Can you please post the output of
```
compiz --replace
```

Ok.. here's the basic process I ran through. 

After i ran "sudo dpkg-reconfigure xserver-xorg -phigh" this is what my xorg.conf looked like. 

```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
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
	InputDevice	"Synaptics Touchpad"
EndSection

```

After doing a ctrl+alt+bksp the desktop loads up without any effects.  I run "compiz --replace" at the term and this is the result that gets output.
 
```

Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

Obviously the effects don't start working with that. 
So I change the xorg.conf manually to use the "ati" driver instead of "vesa" .  To make this longer than necessary, here is that xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
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
	InputDevice	"Synaptics Touchpad"
EndSection
```

After making manual change, saving, and then doing ctrl+alt+bksp, the desktop loads up with effects working.  If it run "compiz --replace" at this point, here is the output: 

```

Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

So at this point effects ARE working for me.  I'm mainly wondering if there are other manual configurations I need/can do to improve performance, since I had to make manual configurations to get it to work at all. 

Again, thanks for all the help, and apologize for the length :)

---

### Post by Rocket2DMn on 2008-05-01
Normally it should have autodetected the "ati" card, I don't know why it opted to use the fallback "vesa" driver, normally that Driver line isn't even there when you reconfigure in Hardy.  Could be because of faulty hardware, a bug in X, or a bug in the ati driver.  As far as the slowness in firefox, I really don't have an answer for you.  You have to remember that this a workaround since the open source drivers are blacklisted for compiz to begin with.
You may consider starting another thread in this forum so others can try and help you, rather than just me.  There have been all kinds of problems with Compiz and Hardy, I'm actually surprised they let Compiz come preinstalled in Hardy which is a LTS version of Ubuntu.  Sorry I couldn't nail it down for you, good luck.

---

### Post by leeyee on 2008-05-02
I can confirm that, after did
```
sudo dpgk-reconfigure xserver-xorg -phigh
```
It gets back 3D acceleration and compiz effect to Hardy (i upgraded from Gusty). However, you still need to do the trick given in the first post to enable compiz. However, I just want 3D acceleration, but not compiz (i am in fluxbox). :-)

P.S. I'm using ATI Radeon 9000.

---

### Post by The_Seeker on 2008-05-03
> **Rocket2DMn said:**
> Did you upgrade from Gutsy?  The new X doesn't like xorg.conf as much as it used to, so you should try reconfigured X to get a more generic xorg.conf and let X do its new autodetection thing at runtime:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
then restart X with CTRL+ALT+BACKSPACE

Hi Rocket,
I did as you suggested. I issued the following command:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```

and the output of my xorg.conf file after issuing the above command is:

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

But when i do enable compiz, the issue with slow scrolling in firefox still exists :( 
Is this a problem with my card? or hardy ?

---

### Post by Rocket2DMn on 2008-05-03
The_Seeker, I honestly don't know - it could be either.  You are not the only person to experience this problem, I have seen other threads with this.  Although I don't know if anybody has found a solution, you should search around to see if you find anything.  If you do find a fix, please let us know.  I really need to start compiling a collection of known (or at least sometimes successful) fixes.

bronsoja, if you are still reading this thread, have a look here: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207)

---

### Post by pmgr33r on 2008-05-05
Tried the above method and recieved this:

pat@Herbert:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.




just wondering what to do fix fix it

thanks

---

### Post by Rocket2DMn on 2008-05-05
It says you are using the fgrlx restricted drivers, what is your video card?
```
lspci | grep VGA
```
Also, have a look at this bug report - [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207)

---

### Post by terrorsathan on 2008-05-05
Hello,

I'm having a problem with my graphics card/drivers, using ATI Radeon HD 2400 XT. When I move any window or if I scroll in a window (f.e. Firefox) a huge flickering appears and it takes a lot of time till the window gets to the place I actually moved it to (I [created a thread]("http://ubuntuforums.org/showthread.php?t=777106") to find a solution for this problem, with no success, yet). I'm _not_ using any special effects or compiz at this time.
I have tried to install drivers with Envy, which didn't work. I also tried to install drivers from the ATI site, which didn't help either (actually I'm not sure if I even installed it correctly (?) ...).

Anyway, "*$ glxinfo | grep -i direct*" returns
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```
As far as I know, direct rendering should return "yes", but I have no clue how to activate it.
I'm new to Ubuntu and all that driver stuff, so I hope someone can help me because I'm really totally lost (and I can hardly use ubuntu with this annoying problem ...).

Thank you.

Best regards,
terrorsathan

---

### Post by Rocket2DMn on 2008-05-05
> **terrorsathan said:**
> Hello,

I'm having a problem with my graphics card/drivers, using ATI Radeon HD 2400 XT. When I move any window or if I scroll in a window (f.e. Firefox) a huge flickering appears and it takes a lot of time till the window gets to the place I actually moved it to (I [created a thread]("http://ubuntuforums.org/showthread.php?t=777106") to find a solution for this problem, with no success, yet). I'm _not_ using any special effects or compiz at this time.
I have tried to install drivers with Envy, which didn't work. I also tried to install drivers from the ATI site, which didn't help either (actually I'm not sure if I even installed it correctly (?) ...).

Anyway, "*$ glxinfo | grep -i direct*" returns
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```
As far as I know, direct rendering should return "yes", but I have no clue how to activate it.
I'm new to Ubuntu and all that driver stuff, so I hope someone can help me because I'm really totally lost (and I can hardly use ubuntu with this annoying problem ...).

Thank you.

Best regards,
terrorsathan

Unfortunately you are asking in the wrong place since this thread is for those using the open source ati drivers which you card does not take.  If I remember correctly, you should be using the radeonhd driver.  You seem to have one of the newer, more advanced cards that is still lacking support in linux.  You might start with removing the proprietary drivers you installed, reconfiguring X (see posts 72 and 73 on this page), then reinstalling the restricted drivers.  Good luck.

---

### Post by terrorsathan on 2008-05-05
> **Rocket2DMn said:**
> Unfortunately you are asking in the wrong place since this thread is for those using the open source ati drivers which you card does not take.  If I remember correctly, you should be using the radeonhd driver.  You seem to have one of the newer, more advanced cards that is still lacking support in linux.  You might start with removing the proprietary drivers you installed, reconfiguring X (see posts 72 and 73 on this page), then reinstalling the restricted drivers.  Good luck.
I see ... didn't know that my card doesn't support open source drivers :(.
Anyway, I'll try to do what you said, lets see if it works.

Thank you.
Best regards

EDIT:
I executed *sudo dpkg-reconfigure xserver-xorg -phigh* which returned
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080505212715

```
Doesn't look too good ...

---

### Post by Rocket2DMn on 2008-05-05
That is normal, it's just making a backup of your existing xorg.conf file in the format of xorg.conf.YearMonthDayTime and replacing xorg.conf with the stuff it's generating.

---

### Post by terrorsathan on 2008-05-05
Ok, so now this is really weird ... after rebuilding xorg.conf with this command and restarting X the flickering is totally gone and everything seems to work fine :o :) ... that's confusing, because after I upgraded to Hardy the flickering appeared, so it looks like the upgrade 'damaged' my xorg.conf ... hmmm ...

Well thank you a lot Rocket2DMn :) easy solution but very effective ;)
Best regards, have a nice day

terrorsathan

---

### Post by RAOF on 2008-05-06
> **terrorsathan said:**
> Ok, so now this is really weird ... after rebuilding xorg.conf with this command and restarting X the flickering is totally gone and everything seems to work fine :o :) ... that's confusing, because after I upgraded to Hardy the flickering appeared, so it looks like the upgrade 'damaged' my xorg.conf ... hmmm ...

Well thank you a lot Rocket2DMn :) easy solution but very effective ;)
Best regards, have a nice day

terrorsathan

More likely is that there was some option set in your xorg.conf which the new ati driver didn't like.  Now that you've regenerated a (practically empty) xorg.conf, the driver's happy again :).

---

### Post by terrorsathan on 2008-05-06
> **RAOF said:**
> More likely is that there was some option set in your xorg.conf which the new ati driver didn't like.  Now that you've regenerated a (practically empty) xorg.conf, the driver's happy again :).
Alright, I see :)
Unfortunately now I get I white screen when I try to activate normal/extra effects or compiz ... let me know if you know a solution for this problem. But well, at least I can use my desktop normally again :)

---

### Post by Swagman on 2008-05-06
I get...
[b][i]

susan@susans-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 1002:5e4b (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No composite extension[/i][/b]

Thats after adding skip checks.
graphics = X700

---

### Post by Dav_Criv on 2008-05-06
Hello, I am rather new to Ubuntu and Linux and I have been studying and reading up on many forums and many problems that have occured with other users configurations. I am having a specific problem with my ATI driver (ATI mobility Radeon 9100. I have tried to follow this thread as best as I could and have had some success. My effects are working now, but when i activate normal or extra effects my computer runs very sluggish. Any ideas what the problem might be?? Second, I dont beleive i can run anything 3D. For example, the chess game that came with Ubuntu works but i can not run under 3D mode. It says that my python openGL is missing or not functioning. Does anyone have any ideas on how to fix this? I am running the open-source drivers, not the restricted ones from ATI.
Thank you,
Dav_Criv

---

### Post by Rocket2DMn on 2008-05-06
> **Swagman said:**
> I get...
[b][i]

susan@susans-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 1002:5e4b (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No composite extension[/i][/b]

Thats after adding skip checks.
graphics = X700

swagman, your video card takes the restricted fglrx drivers, so this isn't the place to get help since we are dealing with the open source drivers here.  However, if you upgraded from Gutsy, you may need to reconfigure X to reset your xorg.conf file
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
then restart X with CTRL+ALT+BACKSPACE.  Then you can try installing restricted drivers using a program called EnvyNG - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
If that doesn't get you going, you should start a new thread on these forums and somebody with more experience with fglrx and compiz can help you out.

> **Dav_Criv said:**
> Hello, I am rather new to Ubuntu and Linux and I have been studying and reading up on many forums and many problems that have occured with other users configurations. I am having a specific problem with my ATI driver (ATI mobility Radeon 9100. I have tried to follow this thread as best as I could and have had some success. My effects are working now, but when i activate normal or extra effects my computer runs very sluggish. Any ideas what the problem might be?? Second, I dont beleive i can run anything 3D. For example, the chess game that came with Ubuntu works but i can not run under 3D mode. It says that my python openGL is missing or not functioning. Does anyone have any ideas on how to fix this? I am running the open-source drivers, not the restricted ones from ATI.
Thank you,
Dav_Criv

Can you please post the entire output of
```
lspci | grep VGA
compiz --replace
```

---

### Post by Dav_Criv on 2008-05-06
Thank you for the quick response!! here is what comes up:

davide@computer:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
davide@computer:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: Segmentation fault
present. 
Checking for non power of two support: Segmentation fault
present. 
Checking for Composite extension: present. 
Segmentation fault
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: Segmentation fault
present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by Rocket2DMn on 2008-05-06
Those segmentation faults worry me, that means the code is either not executing correctly or it is corrupted - that is the first I've seen of it for compiz.  However, it kept going, so we will try, too.  For that GConf backend error, have a look at this bug report - [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207)
The report has a little workaround in it, do let me know if it works.  I'm assuming compiz isn't even starting right now.

---

### Post by Dav_Criv on 2008-05-07
Well, compiz is working and I used the workaround to get rid of the error. That worked but i still get those segmentation faults....here is the output:

Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: Segmentation fault
present. 
Checking for non power of two support: Segmentation fault
present. 
Checking for Composite extension: present. 
Segmentation fault
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: Segmentation fault
present. 
Checking for Xgl: not present. 

Compiz does still work but is running sluggish....
Im going to see if any other users have run into this problem and i will post any new info i get....until then...any ideas?
Dav_criv

---

### Post by Rocket2DMn on 2008-05-07
I'm really not sure what is up with those segfaults, but I know sluggish effects are being reported all over the place, and we have yet to figure out why (you have to remember, we already using a workaround, Compiz does not officially support these video cards).  You mentioned in your first post that it said something about python openGL, do you still get that error?  If so, where, can you show us the command/output?
Also, is your system fully updated?  If you are unsure, run
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Dav_Criv on 2008-05-09
Well....the 3D rendering problem has been fixed....I was just missing some python addons which I downloaded using synaptic manager...
Thank you

---

### Post by adster101 on 2008-05-09
I'm having similar issues here. 

My Laptop is an EVO N600C with a Radeon Mobility M graphics chip. Until I upgraded the desktop effects were working perfectly with the ati drivers. 

I have applied the work around suggested at the beginning of this post and it does seem to work. Now whenever I type fusion-icon the desktop seems to freeze up and stop responding. Then I will have to log off and then log back in. It seems to be worse since I applied the bug fix to the when I switch to Emerald and start using my preferred theme is quite 'buggy' with flashed of the desktop appearing when I maximise a window or the drop shadow effects not working until you click on the window and so on.

It seems OK if I do compiz--replace etc but do I need to do that everytime I log in now?

This is annoying as it was working flawlessly before the upgrade!!

---

### Post by adster101 on 2008-05-09
Well, under compiz the desktop is very flaky. Tooltips break up the page.

---

### Post by adster101 on 2008-05-09
> **Rocket2DMn said:**
> Thank you for the feedback, that sounds like it could be useful for others having trouble after a dist upgrade.  If you have any other threads in which that method has worked for people, please let me know and I will add it to the original post as a troubleshooting method (assuming it's a solid solution).
Commands would probably be something like
```
sudo apt-get remove linux-restricted-modules-*
sudo apt-get autoremove
sudo apt-get install linux-restricted-modules-`uname -r`
```

I entered sudo-apt-get install into a terminal and got this:

The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1 libnss3-0d
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  linux-generic linux-restricted-modules-2.6.20-16-generic
  linux-restricted-modules-2.6.22-14-generic
  linux-restricted-modules-2.6.24-17-generic linux-restricted-modules-common
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 133MB disk space will be freed.

Has this method been tested anywhere else because I don't want to make things worse!

---

### Post by Rocket2DMn on 2008-05-09
adster,
What those commands are doing is removing the restricted modules for all your kernels, cleaning up a little bit, then reinstalling only the restricted modules for the kernel you are using.  Some users reported having problems relating to old restricted modules, though I don't know why, and that seems to have helped some people.  You are not likely to break anything with those unless you revert to using other kernels, in which case you can install the restricted modules for those kernels using the 3rd command when you are booted into those kernels.

---

### Post by adster101 on 2008-05-09
OK I just ran the first two commands but what is the syntax of the third command?

---

### Post by Rocket2DMn on 2008-05-09
The apostrophe like characters are backhashes (I think), the same button as ~ in the upper left of your keyboard.  Using these allows you to run a command within a command (uname -r returns your kernel version).
```
sudo apt-get install linux-restricted-modules-`uname -r`
```

---

### Post by adster101 on 2008-05-10
I tried this and it didn't seem to make much difference. My dekstop is too slow and patchy to allow me to work with it under compiz/emerald. This is mighty frustrating as it worked like a dream under Gutsy.

I was thinking of trying out KDE. Will I have similar problems under KDE?

What is the simplest way to revert back to 7.10 and or what is the liklihood of this being fixed in the next release?

---

### Post by Rocket2DMn on 2008-05-10
KDE is not likely to solve your problem, it may actually make it worse since it requires more system resources than GNOME.  The only way to revert back to 7.10 is to do a fresh install.  I would suggest fresh installing Hardy first to see if that fixes your problem, most of people's issues seem to come after upgrading, not fresh installs.

---

### Post by adster101 on 2008-05-10
OK Thanks, I might try a fresh install of either Gutsy or Hardy then. Bit of a PIA but worth a shot.

---

### Post by feenstra on 2008-05-13
> **Rocket2DMn said:**
> I've seen this a few times, but people haven't gotten back to me.  I need to see the output of
```
cat ~/.gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge
```

produces
```
cat: /home/feenstra/.gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge: No such file or directory
```

However, in gconf-editor there is a key 'initiate_edge' under /apps/compiz/plugins/scale/allscreens/options, type 'list', with its value set to '[]' (an empty list).

Is ccsm barking up the wrong tree here? 

By the way, this is a fresh Hardy install, but my user data is inherited from gutsy (and older). Hope this helps!

---

### Post by feenstra on 2008-05-13
-

---

### Post by Rocket2DMn on 2008-05-13
> **feenstra said:**
> produces
```
cat: /home/feenstra/.gconf/apps/compiz/plugins/scale/allscreens/options/initiate_edge: No such file or directory
```

However, in gconf-editor there is a key 'initiate_edge' under /apps/compiz/plugins/scale/allscreens/options, type 'list', with its value set to '[]' (an empty list).

Is ccsm barking up the wrong tree here? 

By the way, this is a fresh Hardy install, but my user data is inherited from gutsy (and older). Hope this helps!

Hey, here is a related bug report - [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207)

---

### Post by geoffbeaumont on 2008-05-14
> **adster101 said:**
> 
It seems OK if I do compiz--replace etc but do I need to do that everytime I log in now?

This is annoying as it was working flawlessly before the upgrade!!

Has anyone come up with a decent solution for this? Like adster101 (and, I suspect, a lot of other people) I had a perfectly functional compiz before the upgrade. It's not the only problem I've got with Hardy Heron*, but even though it's just eye candy it's actually the most irritating one :(

I could put the command to start compiz from bashrc (not sure if that will cause the screen to blank and redraw still, or if compiz will aready be running in time to avoid this), but this seems like a horrible bodge. How is compiz normally started when it hasn't been crippled?

Does anyone know what the bug(s) that resulted in the compiz team blacklisting the FOSS ati driver are? They must be pretty nasty for them to effectively boot out a large number of satisfied users to avoid dealing with them?

* - Hardy Heron is something of a disappointment for me. I recklessly upgraded from Gutsy Gibbon (after a wait to let early issues be sorted) having got used to Ubuntu releases being really solid. The things that really matter work, but it's pretty ragged round the edges :(

---

### Post by RAOF on 2008-05-14
> **geoffbeaumont said:**
> ...
I could put the command to start compiz from bashrc (not sure if that will cause the screen to blank and redraw still, or if compiz will aready be running in time to avoid this), but this seems like a horrible bodge. How is compiz normally started when it hasn't been crippled?


Following the sticky at the top of this forum, you should be able to put SKIP_CHECKS="yes" in a config file and then compiz will skip the blacklist check.  In that case it'll behave exactly as if your card wasn't blacklisted.

> **geoffbeaumont said:**
> 
Does anyone know what the bug(s) that resulted in the compiz team blacklisting the FOSS ati driver are? They must be pretty nasty for them to effectively boot out a large number of satisfied users to avoid dealing with them?
...

All sorts of things, from X crashes to the system hard-locking.  Furthermore, it was determined that the PCIID of the cards was an inaccurate guide for determining whether a card would exhibit these bugs or not, so it wasn't possible to just disable compiz on the cards with problems.  The thinking was that the inconvenience of having to explicitly disable the blacklist would be better than accidentally missing one of these problem cards, and the system locking up on a semi-regular basis.

---

### Post by adster101 on 2008-05-15
Well my system is usable under compiz and GTK. It seems to be emerald and the theme I was using that pushes it over the edge! :-)

I know that silly effects shouldn't make such a difference but it is surprising how used to them you get. But I got most of what I need with compiz/gtk.

I'm thinking of trying out another linux distro though. Perhaps Debian or Fedora. But I will check that my laptop is compatible with whatever I choose. Then again maybe I will stick with Ubuntu as switching OSs might really screw things up! :-D

---

### Post by odysseusjak on 2008-05-15
The method by RAOF worked perfectly for me.

---

### Post by geoffbeaumont on 2008-05-15
> **RAOF said:**
> Following the sticky at the top of this forum, you should be able to put SKIP_CHECKS="yes" in a config file and then compiz will skip the blacklist check.  In that case it'll behave exactly as if your card wasn't blacklisted.

Okay - I'll give that a try. The first post states that that workaround has been deprecated in favour of the manual one. If it actually works better then why? I can see that trying the first method before editing the configuration file is wise, as if it does go wrong your computer will still work properly next time you start it, but maybe the original version should be 'step two' rather than deprecated?

> **RAOF said:**
> All sorts of things, from X crashes to the system hard-locking.  Furthermore, it was determined that the PCIID of the cards was an inaccurate guide for determining whether a card would exhibit these bugs or not, so it wasn't possible to just disable compiz on the cards with problems.  The thinking was that the inconvenience of having to explicitly disable the blacklist would be better than accidentally missing one of these problem cards, and the system locking up on a semi-regular basis.
Fair enough...that seems like a reasonable basis! :(

It seems like the issue is more poor communication than anything - it's very frustrating to 'upgrade' your system and find it doesn't work as well as before. Ideally the upgrade wizard should have warned about reduced functionality and how to test compiz and permanently enable it if it worked (preferably via a configuration dialogue for the benefit of users who are scared of editing files, since Ubuntu is certainly easy enough for them these days).

Of course, the ideal solution would be to fix the bugs, but I realise that's not controlled by the compiz team, though maybe Ubuntu could have found the resources to do something about it.

In some ways it's not so much irritating on my own account - this laptop is a tool, and the eye candy isn't necessary at all - but because it's what seems to sell linux. I've run linux for years, and windows users have generally been unimpressed. They really don't care that it's faster and more stable, but since gutsy quite a few have been very impressed by how much slicker and more attractive linux is (and that includes vista users).

---

### Post by geoffbeaumont on 2008-05-15
> **geoffbeaumont said:**
> Okay - I'll give that a try.
Nope - that has no effect whatsoever on my machine :(

---

### Post by geoffbeaumont on 2008-05-15
> **geoffbeaumont said:**
> Nope - that has no effect whatsoever on my machine :(
Just sat down and looked at what the replacement fix actually does (yes, I know... :roll:). All it does is place the same switch in a user specific file instead of the global one. So it's not that surprising that which method is used makes no difference to whether compiz starts or not...

So why doesn't compiz start?

---

### Post by geoffbeaumont on 2008-05-15
> **geoffbeaumont said:**
> So why doesn't compiz start?

All becomes clear(ish)! Although the advanced desktop features dialague showed my settings still selected, if I went into the basic default visual effects tab in the appearance dialogue no options where selected (this seems to be normal if you've customised your options from advanced desktop features). I selected 'None' then 'Extra', compiz is now enabled automatically when I log in. Evidentally the upgrade switched a flag somewhere.

There is a minor caveat to this - the apearance dialogue will change some of your advanced desktop features settings, which is annoying but easily fixed. I'm sure there will be a simple config file flag which can be changed instead of this - anyone know where it lives?

---

### Post by RAOF on 2008-05-16
> **geoffbeaumont said:**
> All becomes clear(ish)! Although the advanced desktop features dialague showed my settings still selected, if I went into the basic default visual effects tab in the appearance dialogue no options where selected (this seems to be normal if you've customised your options from advanced desktop features). I selected 'None' then 'Extra', compiz is now enabled automatically when I log in. Evidentally the upgrade switched a flag somewhere.

...

Ah, OK.  This would seem to be a bug in the Desktop Effects code.  It looks like it's got confused somewhere and ended up in an inconsistent state (*one* of the "None", ..., "Extra" options should have been selected ;))

---

### Post by radar.duse on 2008-05-27
...well, after scrutinizing this (and other) threads, it seems RAOF's workaround did the trick for my ATI Radeon 320M card....(thanks RAOF)
...of course you can't have the best of both worlds, so when "Effects" are On everything suddenly goes into s_l_o_w__m_o_t_i_o_n....(during my waiting intervals I am entertained by a nice greying of the active window....) including scrolling etc, etc,
Still, as people above emphasised, it's only eye-candy and it doesn't reduce the real value and quality of ubuntu...  It's just** a small P.I.A.**...
-------------------
*I am using a NEC Versa M320 laptop with 1GB RAM and the above mentioned ATI, with a fresh install of Ubuntu 8.04 dual-booting with windozeXP SP3. Hardy Heron was installed via Wubi (no partition)*

---

### Post by dmizer on 2008-06-02
just wanted to step in and say thanks Rocket2DMn for this fantastic howto and the continued support in this thread.

---

### Post by ToddMax on 2008-06-15
So I would love to get anyone's ideas for troubleshooting my machine.
I've used this howto, but still pretty green to Hardy and Ubuntu in general.
I am having problems with Firefox, as others have, scrolling really slowly, and Im wondering if the Segmentation faults Im getting below, have anything to do with it.  Funny thing is, in xorg.conf, in the Device portion, doesnt list ATI as the driver being used... coincidence?
Here's what I've gotten...
Help!

```

todd@todd-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
todd@todd-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: Segmentation fault
present. 
Checking for non power of two support: Segmentation fault
present. 
Checking for Composite extension: present. 
Segmentation fault
Comparing resolution (1024x768) to maximum 3D texture size (1024): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: Segmentation fault
present. 
Checking for Xgl: not present. 
Segmentation fault

```

---

### Post by arunthegr8 on 2008-06-17
> **Rocket2DMn said:**
> I'm not sure what those font problems are, but I don't think it is an issue, it seems like it may have created the correct stuff for you.  For the rest of the output, I got the same thing, I think this is just normal terminal output.
You should be able to use CF now.  You can setup 4 workspaces by right clicking the workspace switcher applet in the bottom panel and hitting Preferences.  4 workspaces is typical, though it started me with only 2.  You can then enable the cube and other desktop effects using compizconfig-settings-manager - note that it will prompt you to disable Desktop Wall if you enabled the Desktop Cube.

Again, I suggest making launchers in your panels to enable/disable compiz so you can avoid having to run these commands in terminal every time you want to change.
Right click the Panel area and hit Add to Panel, choose Custom Application Launcher and add the compiz/metacity commands from there.

Mine still doesnt work. it just keeps logging off even if i change the settings to normal. in compiz fusion icon window manager is selected as compiz but still it doesnt work. i have an ati x200 onboard gpu.

I dont have the default drivers but have installed a driver with filename <ati-driver-installer-8.42.3-x86.x86_64.run>.

Will uninstalling it work? How do i do it. I m stlii new to linux.

---

### Post by Rocket2DMn on 2008-06-17
> **arunthegr8 said:**
> Mine still doesnt work. it just keeps logging off even if i change the settings to normal. in compiz fusion icon window manager is selected as compiz but still it doesnt work. i have an ati x200 onboard gpu.

I dont have the default drivers but have installed a driver with filename <ati-driver-installer-8.42.3-x86.x86_64.run>.

Will uninstalling it work? How do i do it. I m stlii new to linux.

Hi,
Those drivers that you installed from the .run file are restricted fglrx drivers, not the open source ones which this thread is geared toward.  I suggest removing the drivers you installed with that .run file (it may have an option in the installer, or you may be able to do like "ati-driver-installer-8.42.3-x86.x86_64.run --uninstall" in terminal.  If your card uses restricted drivers, you should try enabling them from System->Administration->Hardware Drivers.  Alternatively, you can use EnvyNG to automatically detect which drivers you should use and have it install them for you - [http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)
Otherwise, you need to start a new thread to get support for using restricted drivers.
Good luck!

---

### Post by Rocket2DMn on 2008-06-17
> **ToddMax said:**
> So I would love to get anyone's ideas for troubleshooting my machine.
I've used this howto, but still pretty green to Hardy and Ubuntu in general.
I am having problems with Firefox, as others have, scrolling really slowly, and Im wondering if the Segmentation faults Im getting below, have anything to do with it.  Funny thing is, in xorg.conf, in the Device portion, doesnt list ATI as the driver being used... coincidence?
Here's what I've gotten...
Help!

```

todd@todd-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
todd@todd-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: Segmentation fault
present. 
Checking for non power of two support: Segmentation fault
present. 
Checking for Composite extension: present. 
Segmentation fault
Comparing resolution (1024x768) to maximum 3D texture size (1024): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: Segmentation fault
present. 
Checking for Xgl: not present. 
Segmentation fault

```

Sorry for the delayed response.
Those segmentation faults are not good, you may want to consider reinstalling compiz:
```
sudo apt-get install --reinstall compiz
```
If that doesn't help, it seems like you have a bigger problem, esp. since you said you are having other problems, too.
If you have xserver-xgl installed, you will want to uninstall that, which may help with your scrolling problem in firefox:
```
sudo apt-get remove --purge xserver-xgl
```
For your xorg.conf, don't worry - that is normal for Hardy, which uses a newer version of X that relies more on autodetection rather than xorg.conf.  We can't complain too much, this is the first version of Ubuntu that these Radeon 9000s worked out of the box with.  You can post your xorg.conf file if you'd like:
```
cat /etc/X11/xorg.conf
```

---

### Post by ToddMax on 2008-06-17
> **Rocket2DMn said:**
> Sorry for the delayed response.
```
sudo apt-get install --reinstall compiz
``` No problem.. I just appreciate the help...Done!

> **Rocket2DMn said:**
> If you have xserver-xgl installed, you will want to uninstall that, which may help with your scrolling problem in firefox:
```
sudo apt-get remove --purge xserver-xgl
``` Done!  So far, no noticable improvement scrolling

> **Rocket2DMn said:**
>  You can post your xorg.conf file if you'd like:
```
cat /etc/X11/xorg.conf
```

Here we go... ```
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by Rocket2DMn on 2008-06-17
OK, that's pretty much what I expected would happen with those commands.  Some people have been able to nail down their problems with FF, but others have not - there really isn't a one-solution-fits-all method of dealing with it.  I suggest using the Search function on the forum to look for other people who have posted about FF being slow with scrolling, you will get a lot of hits.  You can try some of the methods suggested, hopefully something will work.  If not, I don't think you are alone.

---

### Post by ToddMax on 2008-06-17
> **Rocket2DMn said:**
> OK, that's pretty much what I expected would happen with those commands.  Some people have been able to nail down their problems with FF, but others have not - there really isn't a one-solution-fits-all method of dealing with it.  I suggest using the Search function on the forum to look for other people who have posted about FF being slow with scrolling, you will get a lot of hits.  You can try some of the methods suggested, hopefully something will work.  If not, I don't think you are alone.

Thanks for the help.. much appreciated.
Appendix to this... since you know the card Im using (right?) would it be unusual that movements and effects in Hardy are kinda stilted and others are not?  Example... jumping between workspaces as a cube is pretty smooth, but moving a window or maximizing or minimizing is again kinda stuttering and slow.  I just noticed that scrolling within compiz is even slow.
Are my settings chosen all ones to really slow things down or what is going on??
Thanks again!

---

### Post by Rocket2DMn on 2008-06-17
Some effects just require more processing power than others.  You can try fiddling with settings like going to General Options, Display Settings tab and setting Texture Filter to Fast.  I have the 64MB video card size, maybe you have the 32MB, but even mine is a little slow, so I don't actually use Compiz.  IMHO, it looks nice, but gets old and I'd rather have a more responsive machine than a flashy one.  That's not to say I don't show it off :)
You're not the first to complain about some effects being worse than others, it's just the way Compiz is - it really wasn't designed for older machines.  Remember, we are using a workaround just to get Compiz to work at all!

---

### Post by fredunderhill on 2008-07-15
thanks. worked like a charm.

---

### Post by aaronp on 2008-07-25
Hi all,

Having a few issues with this.
I have a Radeon 9600 and the suggested method works ok but I couldn't enable it without the xserver-xgl drivers installed. So I installed them and now suffering from painfully slow rendering and persistent random hard lockups (no alt-ctrl-backspace or alt-ctl-Fkey)

After removing xgl and just using the fglrx ati drivers again everything is ok but I'm keen for the effects. Any other options or am I stuck without any chances here?

thanks
Aaron

---

### Post by Rocket2DMn on 2008-07-25
The Radeon 9600 should be using the restricted fglrx drivers like you said you installed.  How did you install them?  You might benefit from running the compiz-check script - [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by aaronp on 2008-07-25
Thanks Rocket. 

I installed the drivers by: ```
sudo apt-get install xorg-driver-fglrx
``` after enabling the restricted drivers module.

Compiz-check is what led me to try the xgl driver in the first place but without xgl installed I get 'FAIL' on the first check and fifth check.

Funnily enough I upgraded to Hardy from Gutsy since posting here (yesterday) and now running compiz-check (without using xgl drivers) yields all 'OK' results: 

```


Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 AR [Radeon 9600]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

However, I feel there is still something wrong - I am now able to enable the desktop effects without the xgl driver but if I do I am getting some weird misrendered triangles in the corner of my screen randomly upon opening applications and the occasional hard lock when trying to switch between desktops or super-tab between apps. Are there still some settings that I am not getting right?

This is not a deal-breaker because I love Ubuntu but it'a a bit of an annoyance that I can't get it to work even with a card that should allow me to.

thanks again
Aaron

---

### Post by Rocket2DMn on 2008-07-25
aaronp, this is not the best place to seek help with your specific video card.  This thread is for cards using the open source drivers, but fglrx is the restricted ati drivers.  You should start a new thread in this forum so that users more experienced with fglrx can help you out (there should be plenty of them).  Good luck.

---

### Post by aaronp on 2008-07-25
That's fair enough - will do. Thanks Rocket.

---

### Post by RellikZephyr on 2008-07-29
Hi

i am new (very new) to linux and am having the compiz problem

i have tried everything in this thread and nothing has worked

the output from compiz --replace  is...

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:9400 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

incase it helps  video card =  ati 2900XT

output from compiz check is all OK
have tried ati binary X.org drivers, when visual effects activated screen turns all white
have done fresh install of compiz
have updated
have tried everything in this thread   and no go

thanks in advance for help

RellikZephyr

---

### Post by aaronp on 2008-07-29
tried installing xgl?

sudo apt-get install xserver-xorg-xgl


Aaron

---

### Post by Rocket2DMn on 2008-07-29
RellikZephyr,
Your video card does not use the open source ati drivers, so you need to install the restricted drivers from System->Administration->Hardware Drivers.  If you need further help with your card, you should start a new help thread since this one is for cards using the open source drivers only.  Then somebody more experienced with the restricted drivers can help you out.  Good luck.

---

### Post by RellikZephyr on 2008-07-30
aaron p -  i have tried installing them  but when i run script i get output

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-xgl

Rocket2d -   i have tried those restriced drivers, and after restart, ubuntu wont start, gets loading splash screen then goes black screen and hangs       requiring ubuntu reinstall  (on another note, after reinstall i have 2 instances of ubuntu in dual boot screen,  how do i remove dead one??)

RellikZephyr

---

### Post by Rocket2DMn on 2008-07-30
You don't need to reinstall just because the GUI doesn't show up, that can be troubleshot fairly easily actually.  However, you really do need to start a new thread for this problem because this thread is for dealing with open source drivers.  I do appreciate the problems you are having, so I suggest posting in the beginners section of the forum - [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326) and you will certainly get quick help there by users more experienced with restricted ati drivers.  Good luck.

---

### Post by RellikZephyr on 2008-07-30
ok will start a new thread  see how i go

thanks

RellikZephyr

---

### Post by RadenMu'az on 2008-08-01
thanks a lot! I got AIGLX/Compiz running!

I use Xubuntu Hardy on my display-less laptop (read: use external monitor instead) with downgraded Xorg (Gutsy's with Feisty's ATI driver) due to blank screen (a bug with recent Xorg)

After struggling to see things on the screen, I want to start Compiz, but says XGL not present. Have no idea to use AIGLX. After installing XGL, DRI somewhat turned off.
XGL sucks.

---

### Post by wootah on 2008-08-01
I just want to throw this in here, I have had my radeon 9600 (RV350 AR aka: Sapphire x1050) working well with the open source drivers OR the fglrx both without using xgl. I can't get the TV-Out working properly with bigdesktop, but it works ok with dual-screens or clone.

---

### Post by redjoel on 2008-08-10
after having a compiz(fusion) un my hardy, i have just realized that it interfered my other application.
i start my totem video player, but it cannot play any videos perfectly (just play a slow motion and no sound at all)
please help me!!
i restart my computer audio / video is able to play, but after stopping the playlist, it begin the same thing :( (like i've said above)
any help would be appreciated so much!! thanks!!

---

### Post by Rocket2DMn on 2008-08-10
Running compiz can slow down movies and 3d applications, so you should use metacity when use graphics intensive programs, especially on slower computers.  The original post in this thread tells you how to switch between compiz and metacity.

---

### Post by japhyr on 2008-08-24
Thank you so much for this thread.  I have put off trying to figure out compiz for a while now, because there seems to be so much to it.  Now in half an hour I have cool things like the ring switcher!  It's a more efficient work environment, it's fun to use, and certainly catches the attention of anyone looking over my shoulder.  Yay linux!

---

### Post by hardy_gnome on 2008-08-24
hello..
i have problems with compiz fusion...
if i wanna compiz to work i have to run compiz --replace and then it will run, but.. very slow burining efect (if it shows, sometimes it wont) and other (yesterday worked just fine, with no 2 frames per minute, just very good effects)...
i just installed emesene and nothin else...

and if i use fusion-icon the effects enable the minimize, x, and maximize buttons disappear.... and... it all get fcked up...:(:(:confused::confused:

---

### Post by Rocket2DMn on 2008-08-24
hardy_gnome, can you please post the output of these commands:
```
lspci | grep VGA
lsmod | grep fglrx
```
Did you ever attempt to install restricted drivers?  If so, how?  Restricted Drivers Manager?  EnvyNG?  Manually?
Can you also post the output of
```
compiz --replace &
```
You can revert back to no desktop effects with
```
metacity --replace &
```

---

### Post by hardy_gnome on 2008-08-24
lspic | grep VGA
01:00.o VGA compatible controller: ATI tech inc mob radeon x2300

lsmod | grep flgrx

fglrx                   1555468   23
agpgart                   34760   1  fglrx
------------------------------------------------

i havent installed restricted drivers... at least i think so...
if i enter replace command it activates compiz, but everything is so slow.. especial burning effect ( abut 1 frame per 3 seconds).. 

now i uninstalled compiz config because it had to many problems... i will install it tomorow...

> if i wanna compiz to work i have to run compiz --replace and then it will run, but.. very slow burining efect (if it shows, sometimes it wont) and other (yesterday worked just fine, with no 2 frames per minute, just very good effects)...

the real thing that bothers me is that that compiz worked yesterday, and all days before when i installed it.. i was a lil bit slower... (for example: burn effect was running at 20fps instead of 30fps).. nothin big...
but today... literaly 3 fckinfps.... :S

---

### Post by Rocket2DMn on 2008-08-24
OK, you have a card that is using (and should be using) restricted drivers, but this thread is for helping people with cards that need the open source drivers.  I don't have enough experience with restricted ati drivers to support you on this (restricted ati drivers = fglrx).  I suggest starting a new thread for your problem here in the Desktop Effects & Customization forum - [http://ubuntuforums.org/forumdisplay.php?f=330](http://ubuntuforums.org/forumdisplay.php?f=330)

Good luck with your problem, there are plenty of others here that should be able to help you with your card.  And welcome to Ubuntu!

---

### Post by japhyr on 2008-08-26
One of the things I've enjoyed most about using Linux is the stability.  I never notice my system slowing down, and I have never had it freeze up.  I was playing with compiz yesterday, however, and it froze up.  I knew that was a possibility, so I'm just wondering if there are certain combinations of effects to avoid as problematic.  I had used the shift switcher and ring switcher for a couple days with no problem.  I enabled the cube, with rotation, reflection, and 3d windows.  I opened a few applications, spread them over a couple desktops, and while rotating the cube with the mouse pointer the system froze.

Are there certain things I should avoid in compiz?  I have an ati radeon rv250 mobility firegl 9000 card on a dell 600m laptop, running HH.

---

### Post by Rocket2DMn on 2008-08-26
I've run into that problem with freezing during cube rotate, and it appears we are using the same laptop.  Could be a glitch in the open source drivers, which is why compiz stopped support, but that's just a thought.  I guess you could avoid the cube rotate and use the desktop wall instead.

---

### Post by japhyr on 2008-09-01
Here's one more glitch I'm finding:  fringing at the edge of some windows.  I've attached a screenshot of the fringing.  The fringing appears around most windows, and around most dialogs that pop up.  It goes away if I restart.  I'm not sure if it's related to using the cube or not.  Anyone else seeing this?

---

### Post by Rocket2DMn on 2008-09-01
I think that is probably a bug in the open source driver as well, though I've typically seen that behavior with people using the fglrx drivers when they shouldn't.  Intrepid is supposed to have a newer version of the open source ati driver which is supposed to be a lot better, so we'll see.  Maybe you'd like to take the Alpha 4 LiveCD for a spin.

---

### Post by fade79 on 2008-10-30
Hi I tried following the step in your 1st post and it turns on compiz but about 1/6 of the right side of my screen does not seem to work.  It just displays artifacts of whatever window i drag through it but it dosen't display the wallpaper or the panel at the top that shows the time, date, and logoff button.  It is as if my screen is just cut off on the right side.  

Here is the terminal output I get when I tried to activate compiz:

Checking for Xgl: [2] 7163
shyh-jeun@shyh-jeun-laptop:~$ not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


I'm using an ATI Radeon Mobility 9200 on an old Sony VAIO S series laptop and I'm using a clean installation of 8.04 with the default drivers. I would appreciate any help you can give me.

Thanks

---

### Post by jhamric on 2008-11-04
I have an IBM T40 with the Radeon Mobility 7500 card. I too was experiencing slow window moves and Firefox scrolling after upgrading to Hardy from Gutsy. Everything had worked fine under Gutsy. I had tried modifying my xorg.conf six ways to Sunday with no improvement. I tried replacing xorg.conf with a minimalist file. Still no joy. Thought I would just have to live without the desktop effects due to the blacklisting of the video card. But I thought I would try a few of the suggestions in this forum anyhow. The "SKIP_CHECKS" did nothing. Removing the value for initiate_edge marginally improved the situation. But the trick that worked for me was cleaning up previous modules:

Code:

sudo apt-get remove linux-restricted-modules-*
sudo apt-get autoremove
sudo apt-get install linux-restricted-modules-`uname -r`

After that I had speedy Compiz effects back again!:p

Hope this helps someone.

---

### Post by notanerd on 2009-05-17
I can enable compiz, but the desktop seriously screwed afterwards. I tried to attach a screenshot but was told its an invalid file. But basically the screen is randomly pixelated and unreadable. When I put in 'compiz --replace' this is the output 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

and here is my xorg.conf

# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Mobility Radeon 9600"
	Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
	Option          "AccelMethod"    "XAA"
	Option          "EnablePageFlip" "true"
	Option          "TripleBuffer"   "true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Mobility Radeon 9600"
	DefaultDepth    24
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by Rocket2DMn on 2009-05-17
notanerd, it would likely help if you have a default xorg.conf file.  See here - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
Are you using restricted drivers?  If so, how did you install them?

---

### Post by notanerd on 2009-05-17
I ran dpkg-reconfigure xserver-xorg but their was no prompt in it to select a video driver. Regardless my xorg.conf has been changed but I am still having the same problem. I was using catalyst 9.3 for a while but the video playback sucked so i purged fglrx and installed the open source driver with apt-get install xserver-xorg-video-ati

---

### Post by Rocket2DMn on 2009-05-17
Are you using Hardy, or some other release of Ubuntu?  Can you please post the output of:
```
lspci | grep VGA
lsmod | grep fglrx
lsmod | grep radeon
glxinfo | grep direct
```

---

### Post by notanerd on 2009-05-17
i'm using Intrepid

evan@durruti:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
evan@durruti:~$ lsmod | grep fglrx
evan@durruti:~$ lsmod | grep radeon
radeon                147616  2 
drm                    86056  3 radeon
evan@durruti:~$ glxinfo | grep direct
direct rendering: Yes
evan@durruti:~$

---

### Post by Rocket2DMn on 2009-05-17
In the past couple of years, I have seen a number of people having problems specifically with their Radeon 9600 cards - some people's work, others' simply don't.  I'm afraid I don't have a solution for you, so I won't drag this out here.  I suggest that you start a new thread specifically for your problem as this one is meant for Hardy and enabling compiz to run, not troubleshooting it.  Sorry, and good luck.

---

### Post by notanerd on 2009-05-17
No worries, thanks for your effort anyway. I think it is a lost cause, and I don't care that much really. I can live without fancy effects.

---

