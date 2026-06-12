---
title: "HOWTO: EDGY OFFICIAL Compiz with new nvidia driver and without XGL/AIGLX"
date: 2006-09-23
forum: General Help
---

### Post by NNois on 2006-09-23
This compiz version is way stable than beryl, it's for people who want compiz simply and faster.
This methode is 100 % working with the new nvidia driver and with the original compiz on my 3 computers:

install the nvidia-glx beta drriver:
add this to your soucre list:
"deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm"

add this to your source list:
"deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy ." don't forget the "." in the end

then:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Install compiz-freedesktop packages :
```
sudo apt-get install gnome-compiz-manager compiz-freedesktop compiz-freedesktop-gnome
```

Your Xorg.conf:
Add the following line to my "Screen" Section:
```
Option "AddARGBGLXVisuals" "True"
```

Kill X restart your session and type in a terminal for testing:
```
gnome-window-decorator & compiz --replace --use-cow gconf
```
Now, normally "compiz-tray-icon" is on your startup programs
You just have to restart your session then, click on the compiz tray icon and select "GL Desktop" that's all !
no need to add the compiz --replace stuff in your startup programs...

---

### Post by saracen on 2006-09-23
Why does your repository modify gnome-session?

---

### Post by NNois on 2006-09-23
this is the "bleeding-edge freedesktop.org" versions of compiz
I think your gdm when started is already accelerated...

---

### Post by saracen on 2006-09-23
Yes I know.  I installed those three compiz packages and everything works great.  Thanks.  But what I want to know is why the gnome-session package wants to be updated by your repositories.

---

### Post by saracen on 2006-09-23
By the way, do u know how to get rid of the tearing?  Also, I didn't start compiz with the --use-cow paramater.  In fact, I didn't start it from the command line at all.  I started it from the system tray icon.  Does that use the --use-cow paramater?  If not how do I make it use it?

---

### Post by NNois on 2006-09-23
Sorry but it's not my repository. All can i tell you is that i have updated this package without any problem...
All I want in this post is to share my experience of this day, tring to find a clean methode to use this new nvidia driver.
I've simply found this methode the best because it was no hack at all.

PS: Sorry for my bad english

---

### Post by NNois on 2006-09-23
I have no tearings ...

---

### Post by btdown on 2006-09-23
The method above "works", however, none of my windows have have the Minimize/Maximize/Close window border, and when I open up a terminal window there's only white space...(no terminal window).

Any Idea how to fix?

At least this method doesnt segfault like the other how-to that's posted in the edgy forum, even though that one seemed to have more features (themes/etc).



Edit: I'ts Working! Once I added this line to /etc/X11/xorg.conf under the "ServerLayout" section and restarted everything, I regained my window frames and the white screening went away:
> Option "AIGLX" "true"

---

### Post by JackDog on 2006-09-23
Is there any way to theme this version of compiz? 

Like this: [http://www.gnome-look.org/content/show.php?content=45690](http://www.gnome-look.org/content/show.php?content=45690)

---

### Post by Amaranth on 2006-09-24
No, this version of compiz does not use cgwd. Check out the sticky post at the top of this forum for a repo for my linux-restricted-modules packages and beryl (compiz fork) packages that work with the new drivers.

---

### Post by TravisNewman on 2006-09-24
I have also stuck this thread, and tagged it "OFFICIAL Compiz" to eliminate confusion

---

### Post by TravisNewman on 2006-09-24
Also, just to clarify, with this howto you ARE using AIGLX, it's just that the AIGLX patches are now in X.org so there's nothing you have to do to actually install AIGLX. it is still there though :)

---

### Post by Amaranth on 2006-09-24
Actually, AIGLX is not required to use compiz with nvidia's drivers. Apparently AIGLX is a driver thing that GLX_EXT_texture_from_pixmap is implemented on top of in the open-source DRI drivers. nVidia's drivers support GLX_EXT_texture_from_pixmap in both direct and indirect mode.

---

### Post by NullFile on 2006-09-24
I would like to use this method, but not having themes support is a bummer.
It is faster then beryl+aiglx (well for me it seems that way). I just don't understand why there has to be so many different versions. [-X

---

### Post by Paulus on 2006-09-24
If you use this method and the other guide (below this one) and add the beyrl resporitory to your sources then you can have standard X server with beryl!

[[IMG]http://img84.imageshack.us/img84/1641/screenshot1su4.jpg[/IMG]](http://imageshack.us)

---

### Post by hugmenot on 2006-09-24
I&#8217;d like some clarification, please.
Is this method the preferred method over the XGL+Compiz+Mesa+GLX method in terms of 1. performance, 2. future-proof-ness, 3. compatibility?
Do I need to roll-back changes in 1. my xorg.conf (could someone post a complete file, please?), 2. my installed packages (should I remove stuff or can it remain intalled in case this doesn&#8217;t work?)

---

### Post by mesh on 2006-09-24
Im not sure, but this is what ive done and what im doing. I origionally setup compiz with this guide

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

And i must say, it freakin rocks. :D. Now im going to do this method


[http://ubuntuforums.org/showthread.php?t=244559&highlight=gnome-compiz-manager](http://ubuntuforums.org/showthread.php?t=244559&highlight=gnome-compiz-manager)

Then im gonna try the method explained in this post. Im doing it as we speak. Ill post the results. Peace

UPDATE: Wow, my installation got screwed up already. After sudo apt-get dist-upgrade and a reboot. My windows manager got screwed bad :D. Cant even move windows. Oh well, i have an image of teh fresh install. Gonna reinstall and try this new official meth.


UPDATE: I tried running linux restricted 2.6.17-9 generic.deb and i got a dependency error. Any ideas?

---

### Post by NNois on 2006-09-24
in terms of performance this methode if far away over beryl, windows resizes etc are faster. I think beryl need some improvements...

---

### Post by ~LoKe on 2006-09-24
> **NNois said:**
> in terms of performance this methode if far away over beryl, windows resizes etc are faster. I think beryl need some improvements...

Duh.  Beryl isn't even in it's Alpha stages yet.

---

### Post by scotty2hott2k on 2006-09-24
if anyone is getting tearing, i seemed to fix it by opening up gconf-editor then going into programs->compiz->screen0 (not might not be exact) then unticking autodetect refresh rate and setting my own refresh rate.

---

### Post by saracen on 2006-09-24
> **scotty2hott2k said:**
> if anyone is getting tearing, i seemed to fix it by opening up gconf-editor then going into programs->compiz->screen0 (not might not be exact) then unticking autodetect refresh rate and setting my own refresh rate.

Tried that... didn't help.  Still have serious tearing issues :confused:

---

### Post by Paulus on 2006-09-24
> **scotty2hott2k said:**
> if anyone is getting tearing, i seemed to fix it by opening up gconf-editor then going into programs->compiz->screen0 (not might not be exact) then unticking autodetect refresh rate and setting my own refresh rate.


YES!!!!  thanks for this... I was seriously thinking of going back to xgl.  But now it's silky smooth.  Thankyou very very much!   :cool:

[saracen]("http://ubuntuforums.org/member.php?u=81226"):  You could try messing with some nvidia-settings; I turned on every option that said anything related to v-sync.  Hope this helps.

---

### Post by PriceChild on 2006-09-24
> **NNois said:**
> in terms of performance this methode if far away over beryl, windows resizes etc are faster. I think beryl need some improvements...
The repositories in my thread for beryl have been updated, and an xorg fix added.

Its now incredibly faster than before, and in my opinion faster than on my dapper/xgl partition.

Also added are 64big repos for the -8 kernel :) (-9 lrm is broken)

---

### Post by alcamus on 2006-09-24
This method seems quite a bit faster to me than the one I was using in Dapper. While I liked the variety of themes in what is now called Beryl, the performance hit seemed quite a bit greater. This is pretty sweet and doesn't seem to slow me down.

In any event I hope forking Beryl away from the "official" version won't result in the sort of clashes that exist between some users of Gnome and some users of KDE. Choice is good.

---

### Post by MarkSheely on 2006-09-25
I'm not sure what I'm doing wrong here...

I add the following line to /etc/apt/sources.list:

```
deb http://gandalfn.club.fr/ubuntu edgy
```

and then when I proceed, I get the following error:
```

marksheely@marksheely-laptop:~$ sudo apt-get update
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse) 
```

I'm probably making a pretty simple mistake here.....If anyone could offer some help, I'd really appreciate it.

Thanks,
Mark

---

### Post by alcamus on 2006-09-25
Be sure to add the period at the end of the line:

```
deb http://gandalfn.club.fr/ubuntu edgy .
```

---

### Post by ekerazha on 2006-09-25
Instead of Compiz... why not the new Metacity with compositor?

---

### Post by hoosfoos on 2006-09-25
When I enter the line,

gnome-window-decorator & compiz --replace --use-cow gconf

my whole screen turns white and there is nothing else visible except for the white.  I can rotate the screen with the cube effect but it doesn't do much good as there is only whiteness.
Fortunately restarting x puts me back at a plain non-compiz gnome.

---

### Post by NNois on 2006-09-25
did you have xorg 7.1 (are you in edgy...) ?
I think no because if you have installed the latest version of the nvidia driver it should work without white screen.

Anyway, in this case you think you have to enter in your xorg.conf in "ServerLayout"
```
Option "AIGLX" "true"
```

in the case you haven't compiz from freedesktop.org you have to add olso this line in your "Screen" section
```
Option "DisableGLXRootClipping" "True"
```

Hope it helps...

---

### Post by hoosfoos on 2006-09-25
I'm in Edgy, I installed the latest version of the nvidia driver, I followed the guide at the beginning of this thread to the letter.  I added 
Option "AIGLX"  "true"
to "Server layout" in xorg.conf

I added the line
Option  "DisableGLXXRootClipping"  "true"
to "Screen" in xorg.conf

Still white screen. :(

---

### Post by MarkSheely on 2006-09-25
I had problems until I changed the default depth in my xorg.conf file from 16 to 24.  Not sure why it would make a difference, but it made a HUGE difference.  

Many thanks to the creator of (and contributors to) this thread!

--Mark

---

### Post by pomalin on 2006-09-25
mmmm, compiz can now support metacity's themes. :D

---

### Post by zAo on 2006-09-26
Thanks. Worked.
Scrolling is now fast, but moving windows is a little laggy. (GF6600GT, AMD 2100+ 1GB)

---

### Post by DeeZiD on 2006-09-26
Uncheck "vsync" and "detect refresh rate".
And use the right refresh rate value.

Then it will be even faster than on xgl. :)


regards Dennis

---

### Post by zAo on 2006-09-26
> **DeeZiD said:**
> Uncheck "vsync" and "detect refresh rate".
And use the right refresh rate value.

Then it will be even faster than on xgl. :)

regards Dennis
Thanks Dennis. Will try that later today.

---

### Post by hoosfoos on 2006-09-26
After ending up the a pure white screen everytime I activated compiz,
I finally got everything to work by doing the Beryl Howto
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

I also deleted the enable composite line in my xorg.conf, so one of those two actions got everything to work. :)

---

### Post by puppy on 2006-09-27
Hi everyone, well last night I rather foolishly allowed the system to do a dist-upgrade without making a careful check on what was being updated...  on restart no X  :rolleyes: 

Turns out that the upgrade reinstalled the old nvidia kernel module (8774 I think) ... is it just a matter of downloading the nvidia deb package referred to in the first post and doing a dpkg -i [nvidia filename] from the command line to get the X server back again?

(Pups reminds himself *again* to check suggested upgrades before letting them loose on his system in future ](*,)  )

Any advice appreciated

---

### Post by PriceChild on 2006-09-27
Whoops.

---

### Post by Amaranth on 2006-09-27
You have to use the l-r-m that's in my repo.```
deb http://dev.realistanew.com/beryl edgy beryl
```It's been updated for -10.

---

### Post by puppy on 2006-09-27
Great Amaranth, thankyou - just to clarify, would that be the following file: 

nvidia-glx_1.0.9625...  .deb dated 26 Sept, size 4.3MB ?

---

### Post by Amaranth on 2006-09-27
You need nvidia-glx, linux-restricted-modules-2.6.17-10-generic and linux-restricted-modules-common.

---

### Post by ekerazha on 2006-09-27
Are there "official compiz" packages for Edgy/AMD64 ?

---

### Post by puppy on 2006-09-27
Amaranth, I added the repository to my sources.list, did an apt-get update and an apt-get upgrade and all was sorted - many thanks  :D

---

### Post by brodock on 2006-09-28
blank screen, tryied ALL information found here (ubuntuforums) and at beryl-project forums...

didn't get working on my geforce mx 5200
any idea?

```
brodock@uocentral:~$ glxinfo |grep direct
direct rendering: No

```

---

### Post by PriceChild on 2006-09-28
> **brodock said:**
> blank screen, tryied ALL information found here (ubuntuforums) and at beryl-project forums...

didn't get working on my geforce mx 5200
any idea?

```
brodock@uocentral:~$ glxinfo |grep direct
direct rendering: No

```
Please could you ensure that you've added the "nvidia" driver to your xorg.conf instead of "nv"

Pricey

---

### Post by brodock on 2006-09-28
i did
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "v4l"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
        Option          "XkbModel"      "abnt2"
        Option          "XkbLayout"     "br"
        Option          "XkbVariant"    "abnt2"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
        Option          "Buttons"               "7"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option         "NvAgp" "1"
        Option         "NoLogo" "on"
           VideoRam    128
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "SyncMaster 753v"
    Option        "DPMS"
    HorizSync    30-68
    VertRefresh    50-85
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "SyncMaster 753v"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
Option "AddARGBGLXVisuals" "True"

EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

```

and this is my gdm.conf-custom (modified for use Xgl and old Compiz-Vanilla)
```

# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]
SoundOnLoginSuccessFile=/usr/share/sounds/login.wav
SoundOnLoginFailureFile=/usr/share/sounds/warning.wav
GraphicalTheme=morning

[chooser]

[debug]

[servers]# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true

```

---

### Post by puppy on 2006-09-28
This might not solve your problem, but I notice you have lots of those "wacom" device lines in your xorg.conf (including some towards the end of the file) - I stripped all of those out without ill effects (can someone remind me why they're added in the first place??)

I have a further issue - I want to try the Beryl method (because it has more bells and whistles than the official compiz manager) - having followed the instructions in the first post in this thread, can I just follow the instructions in the Beryl thread to get that version up and running, or do I have to reverse some of the things I've done before starting down that path?

---

### Post by brodock on 2006-09-28
i solved the problem using gdm-custom.conf withou Xgl instructions... now it works faster and no more blankscreens :D

i will remove those wacom lines too, thanks for pointing...

gnome-compiz is good, but compiz-vanilla was a little more updated... like, gnome terminal with true transparency.

---

### Post by PriceChild on 2006-09-28
> **puppy said:**
> I have a further issue - I want to try the Beryl method (because it has more bells and whistles than the official compiz manager) - having followed the instructions in the first post in this thread, can I just follow the instructions in the Beryl thread to get that version up and running, or do I have to reverse some of the things I've done before starting down that path?Yeah you can just follow my thread.

It will also work on the new -10 kernel for you... this guide is now a bit outdated :s

---

### Post by moclippa on 2006-10-01
I installed using these repositories today and they installed some upgrades which caused conflicts in my desktops panels as well as my nvidia drivers. I was having a lot of problems updating things after that and I found that quoting out the new repositories here helped a lot. 

Following quoting out these repositories most of my conflicts were solved during further updates of other components, can't talk specific, but some libs and the nvidia drivers.

I know its helped a lot of people, so don't mean to offend anyone, but it caused me more harm then good!

---

### Post by RAOF on 2006-10-01
> **ekerazha said:**
> Are there "official compiz" packages for Edgy/AMD64 ?

There are now:  [raof.dyndns.org/falcon](raof.dyndns.org/falcon), or the mirrors [ubuntu.moshen.de](ubuntu.moshen.de) and [ubuntu.systemadministrator.org](ubuntu.systemadministrator.org).  (Section: Edgy->Eyecandy)  Note that I don't have AMD64 builds of Amaranth's linux-restricted-modules in there.

---

### Post by dgorchak on 2006-10-01
Need some help: I use KDE (Kubuntu Edgy 6.10 beta), what do I need to change or it's better for me to install Beryl?

As I understand:

_sudo apt-get install gnome-compiz-manager compiz-freedesktop compiz-freedesktop-gnome_ goes to 

**sudo apt-get install compiz compiz-plugins compiz-kde**

I worry about this:
gnome-window-decorator & compiz --replace --use-cow gconf

kwin & compiz --replace --use-cow ???? (what needs to be here?)

---

### Post by ramiro on 2006-10-02
ok a few things:

1) the title for this thread is wrong, it's actually using AIGLX to render (the GLX_EXT_texture_from_pixmap extension is what allows the nVidia drivers to use AIGLX, which has been included in the 9xxx series of drivers. Hopefully these are officially included into edgy quickly). Anyone have any ideas when these rivers will be available in the repositories?

2) the link at the beginning has a link to the restricted modules for 2.6.17-9, whereas edgy now runs 2.6.17-10. is there an updated version anywhere?

3) the reason why you need to run at 24 bit colour depth, is because the last 8 bits are the alpha channel, which are used to indicate transparency. Without it, there is no transparency (and I have no idea how compiz handles it. If it's not working make sure you have your colour depth set to 24 bits)

*edit: oops, 32 bit is alpha, 24 bit is without alpha. you need to do     Option "AddARGBGLXVisuals" "True" to enable 32 bit colour. I imagine with 16 bit colour depth this is impossible still...*

4) apparently gnome-window-decorator is perfectly happy to run in kde.

---

### Post by scotty2hott2k on 2006-10-02
ramiro, actually you are wrong on 1) nvidia has built in support in their drivers for the gl_ext_from_pixmap which means that aiglx is not needed.

---

### Post by RAOF on 2006-10-02
> **scotty2hott2k said:**
> ramiro, actually you are wrong on 1) nvidia has built in support in their drivers for the gl_ext_from_pixmap which means that aiglx is not needed.

No, he is correct.  Lets break it down: AIGLX is **A**cellerated **I**ndirect **GLX**.  Basically, it means: you can use the OpenGL acceleration of your fancy graphics card **without** the program having to talk directly to the card.  So, it can go through the X server.  So, programs **on** the X server, like compiz, can mess with it.

For those playing at home, the nVidia drivers don't implement AIGLX the same way other Xorg drivers have to, and have apparently been able to do it for some time.

GL_EXT_TEX_FROM_PIXMAP is a GL extension which gives the graphics drivers some way of translating from an X pixmap (which is what X uses to buffer windows) to an OpenGL texture, which is what the graphics card understands.  Technically, you could do all the compiz effects without it, but it'd be really slow; the compiz-like-program would need to manually build OpenGL textures from X pixmaps, use them on the graphics card to do the GL rendering, then translate them back to X pixmaps.  Compiz, therefore, doesn't run without GL_EXT_foo support from the drivers.

XGL has a software implementation of GL_EXT_foo shimmed in there, so you could run compiz on XGL without driver support.  Now that there **is** driver support, you don't need XGL for that reason.  (I'll leave whether or not you want all your X rendering to go through OpenGL for another time ;)).

---

### Post by hanzomon4 on 2006-10-02
I can't glxinfo
```
glxinfo |grep direct
glxinfo: /usr/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```
:confused:

---

### Post by scotty2hott2k on 2006-10-02
this is a quote form an nvidia employee on the nvnews forums

> 

Neither Xgl or AIGLX are required to use compiz with the NVIDIA drivers now that they natively support GLX_EXT_texture_from_pixmap.

Xgl is an X server that renders using OpenGL and runs on top of another X server. It was the first X server available to support GLX_EXT_texture_from_pixmap.

AIGLX stands for Accelerated Indirect GLX. It is not related to compiz or GLX_EXT_texture_from_pixmap at all, except that support for GLX_EXT_texture_from_pixmap in the open source DRI OpenGL drivers required it. NVIDIA has always supported Accelerated Indirect GLX rendering.

NVIDIA supports both Direct AND Indirect rendering with the GLX_EXT_texture_from_pixmap extension. Users should not need to install any additional software to run compiz with new NVIDIA drivers. Please see the just-created sticky thread covering the basic setup steps.


---

### Post by jimbob on 2006-10-02
Installed Edgy from downloaded and burned CD and looks real good.

Installed everything called for in first post above and I do have the little red cube on the taskbar but on the lower taskbar I only have (2) selectable windows.

How does one get a cube from only two desktops?

Am I missing something here?
________________________________       
  If I can't be Mr. Root I won't play ...

---

### Post by forcotton on 2006-10-02
You get a plane with each side being one of your desktops.

---

### Post by ramiro on 2006-10-02
nvidia never supported AIGLX until the 9625 drivers so I don't know what that nvidia employee is talking about. You can't run AIGLX on any older version of the drivers because of the missing GLX_EXT_etc 

And the 2 desktops are enforced by metacity. Once you replace it with compiz you'll have at least four desktops since compiz doesn't support any less than 4

---

### Post by RAOF on 2006-10-02
> **scotty2hott2k said:**
> this is a quote form an nvidia employee on the nvnews forums

> ...NVIDIA has always supported Accelerated Indirect GLX rendering.
The acronym of which is... AIGLX.

Although, what he actually means is: "You don't need an X server which supports AIGLX, 'cause we've implemented it in a different way on our own".

---

### Post by ramiro on 2006-10-03
> ...NVIDIA has always supported Accelerated Indirect GLX rendering.

get AIGLX running on the 8xxx drivers and let me know how you go

---

### Post by _simon_ on 2006-10-03
wrong place.

---

### Post by Amaranth on 2006-10-03
> **ramiro said:**
> get AIGLX running on the 8xxx drivers and let me know how you go
AIGLX != what's needed to make beryl/compiz work

AIGLX is the neat thing that lets you play a 3D game at work that's running on your home computer.

---

### Post by scotty2hott2k on 2006-10-03
ramior you are wrong nvidia has nearly always supported aiglx just not that 1 extension (which is required by compiz NOT aiglx).

---

### Post by jimbob on 2006-10-03
forcotton:  So what happened to the fully functional cube I had in Dapper when I installed XGL/Compiz ??

Is this supposed to be beryl now?  What does this really do for me?  I don't even have the wobbly windows anymore.

---

### Post by dpw2atox on 2006-10-03
Could you make some debs for AMD64? I'd love to use the official compiz as beryl has been pretty unstable for me.

---

### Post by RAOF on 2006-10-03
> **dpw2atox said:**
> Could you make some debs for AMD64? I'd love to use the official compiz as beryl has been pretty unstable for me.

You mean, like the ones in this post? :) [http://www.ubuntuforums.org/showpost.php?p=1569848&postcount=51](http://www.ubuntuforums.org/showpost.php?p=1569848&postcount=51)

---

### Post by brodock on 2006-10-04
how to get the latest nvidia driver to work with the latest edgy updates?
(my current dist-upgrade wants to remove nvidia-glx i got from amaramths...)

---

### Post by Amaranth on 2006-10-04
Don't upgrade linux-restricted-modules right now. The newer versions only contain changes for powerpc so there is no reason to.

---

### Post by ~LoKe on 2006-10-04
I'm having problems playing OpenGL games, specifically UT2K4.  A few seconds into the game, it'll freeze up for 10 seconds, unfreeze, then freeze up again.  I have to enable Software rendering instead of OpenGL to be able to play.

Am I doing something wrong?

---

### Post by Melvil on 2006-10-05
```
$ libGL warning: 3D driver claims to not support visual 0x4b
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0

```

What's wrong here? The OSS radeon driver DOES support this extension, beryl works fine.
I'm running AIGLX (edgy)

---

### Post by NoTiG on 2006-10-06
do i really have to downgrade my kernel to 2.6.17-9  for this to work?

edit : nm........ i got amaranths beta nvidia driver instead

edit: while this is cool, the kernel that you need to install for it doesnt support SMP... so it only uses one of my processors..... the --use-cow option or whatever when i typed it from the command line after killing x said "could not open display" ... but every thing still seems to work regardless so im not sure what that command does.

---

### Post by Amaranth on 2006-10-07
```
deb http://amaranth.selfip.com/ edgy lrm
```
Contains linux-restricted-modules for the latest 386 and generic kernels. No more beryl in my repo, only l-r-m.

---

### Post by NoTiG on 2006-10-07
is anyone else unable to right click and rename folders with xgl enabled?

---

### Post by nazgum on 2006-10-07
AIGLX seems to suffer from a similar problem XGL initially experienced; under cpu load it would lag.

XGL ended up fixing this problem a few months in; but AIGLX seems to preform very poorly under load.

Specifically running Ruby on Rails on localhost, whenever dispatch.cgi would run due to me accessing it; the cpu would jump to 30-40% and AIGLX would freeze for a couple seconds.

Anyone else experiencing this?

---

### Post by Amaranth on 2006-10-07
You need the libxorg-sched-hack0 package from the beryl repo to fix that.

---

### Post by ~LoKe on 2006-10-07
> **~LoKe said:**
> I'm having problems playing OpenGL games, specifically UT2K4.  A few seconds into the game, it'll freeze up for 10 seconds, unfreeze, then freeze up again.  I have to enable Software rendering instead of OpenGL to be able to play.

Am I doing something wrong?

Still having this problem. :(

---

### Post by Amaranth on 2006-10-07
Try the sched hack package I mentioned in my last post.

---

### Post by nazgum on 2006-10-08
Thanks Amaranth =)

That did indeed fix it.

---

### Post by NoTiG on 2006-10-08
My only complains so far: windows load without title bars (this only happened after i messed with themeing) , cannot right click on files and rename the folders on the desktop, cannot use some of the themes i could for compiz (i liked the Human theme for compiz)

---

### Post by mthaddon on 2006-10-10
Still can't seem to get the water or zoom plugins working, which I think may be related to the fact that the "Windows" key doesn't work. This used to be an old issue with XGL/Compiz for NVidia. Is this still the case, or do I just have some crud somewhere that is disabling my Windows key (and if so, how do I get rid of that?)

Thanks, Tom

---

### Post by VFiend on 2006-10-11
> **NNois said:**
> Your Xorg.conf:
Add this to the end
```
Section "Extensions"
Option "Composite" "Enable"
EndSection
```

I believe Composite is enabled by default now so this is not needed.

---

### Post by Paool on 2006-10-11
great howto, thanks!:KS

---

### Post by dpw2atox on 2006-10-12
I have a problem with compiz and full screen opengl apps. When I am not using compiz, all 3d acceleration works fine, however when i switch over to compiz and try to open an opengl app in fullscreen, i get terrible performance and continue to have performance issues till i close out of compiz.

One example program is gnome-screensaver. If i open up the screensaver its fine but if I click for a preview, the menu bar that normally is across the top is in the middle of my screen and everything starts to run very slow. I have to kill compiz to fix the performance issue.

I also am getting very slow performance and the same issue with World of Warcraft in cedega.

I have the following lines added to my xorg.conf file

Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"

again this issue only happens when i try and open an opengl window in fullscreen and everything seems fine in windowed mode.


My desktop hardware is:
AMD Athlon 64x2 3800+
Geforce 7600GT 256MB Pci-e
Asus A8NSLI-Deluxe
2GB ddr400
74GB 10,000 raptor sata
Resolution: 1600x1200
OS: Ubuntu Edgy 6.10 

My laptop hardware is
AMD Athlon Turion64 MK-36(2.00GHz)
512MB DDR2 533Mhz
NVIDIA GeForce Go 6150 (shared but up to 128MB)
80GB 5400rpm sata
Resolution: 1280x800
OS: Ubuntu Edgy 6.10


Any ideas?

---

### Post by jrickmar on 2006-10-12
I'm running Dapper Drake in VMware 5.5 on Windows XP.  Is there any way that I can get all this Compiz stuff?  Or am I stuck using Metacity because VMware won't support OpenGL and hardware accelaration?

---

### Post by mthaddon on 2006-10-12
If you do get that working it'd be a work of magic. I don't even know if it's possible, but given that the graphics card supplied to a VM is virtualized I think VMWare would have to ship an OpenGL compliant driver and god knows what else would need to happen. I may be wrong, but I'd find it very hard to believe it's possible.

Having said that I can run Windows in a VM on Linux and simulate wobbly windows, transparency, etc. on the entire Windows OS (i.e. as one app). Which is nice :)

---

### Post by barrosz on 2006-10-13
since todays update to edgy i get a white screen after beryl loads, i know this probably has been asked before but does anyone know what to do? ive been away all summer and i was trying out edgy but yesterday i got puzzled by this, i know that the update included libgl1-mesa-glx and dri and prolly has something to do with the white screen thing but how can i fix this?

---

### Post by dpw2atox on 2006-10-13
barrosz, did you install the nvidia drivers manually or through a package? if you did it manually then you need to reinstall your driver as the mesa package overwrote parts of it.

---

### Post by ubuntu_demon on 2006-10-15
I unstuck the Beryl and Compiz stickies from the Edgy section:
- Edgy stickies became cluttered
- **They are still linked in the README FIRST sticky**
- most interested people should be subscribed by now
- they are popular threads with a lot of posts so they will be found easily

---

### Post by jonah1980 on 2006-10-15
this is awesome, but how come when i tick for gl desktop, on reboot i don't get a gl desktop - i then have to goto tray icon and click it on again.

surely there is a way to startup with this on

tried

compizstart and compiz-start in sessions dialog but these don't work.

can anyone help me thanks??

---

### Post by Vagabund on 2006-10-21
I have the same problem, after every new login i must activate the GL-Desktop to see the effects. How is it possible to activate this permanently? Can anybody help?

Regards
Michael

---

### Post by Shadowline on 2006-10-21
Johan1980 and Vagabund....Goto System/Preferences/Sessions/, open the Startup Programs tab, click the "Add" button, insert "beryl-manager" and restart gnome. Should start up then no problem. :D

---

### Post by Vagabund on 2006-10-21
> **Shadowline said:**
> Johan1980 and Vagabund....Goto System/Preferences/Sessions/, open the Startup Programs tab, click the "Add" button, insert "beryl-manager" and restart gnome. Should start up then no problem. :D

Beryl-manager? I don't have installed beryl, and i don't will do it. Read the first post.

Michael

---

### Post by Shadowline on 2006-10-21
my bad, got beryl on the mind I guess.... try using "compiz --replace --use-cow gconf" instead of beryl-manager like in my previous post. Sorry for the confusion.

---

### Post by Vagabund on 2006-10-21
Thanks Shadowline for the tip. Works fine:D .

Regards
Michael

---

### Post by skroll on 2006-10-21
I have to say, I was using Beryl for awhile, but didn't like how much eyecandy it was bringing to the table.  The official compiz branch seems to be more what I'm looking for, especially since it lets me use my own metacity themes.  Feels much quicker to me, especially since I'm not on the fastest hardware.

---

### Post by PriceChild on 2006-10-26
*moves*

---

### Post by findus on 2006-10-26
Fantastic guide!  I was using Beryl before, and although I am sure it will be fantastic further down the line, this official compiz is a delight!  Cheers guys!:)

---

### Post by oasiscity on 2006-10-26
Hi, I follow this guideline and it works!

but, I notice one problem.

While Compiz is working, I switched to a console using "Alt+F1" to do something.
but when I try to get back to GUI by "Alt + F7", it brings me a black screen. and I can do nothing then.
I want for several minutes, and I am not patient one so I reset my computer :-)

it seems that there is no problem with these kind of switches when the GL Desktop is disabled.

Anyone has the same experience? any idea?

---

### Post by PriceChild on 2006-10-26
> **oasiscity said:**
> Hi, I follow this guideline and it works!

but, I notice one problem.

While Compiz is working, I switched to a console using "Alt+F1" to do something.
but when I try to get back to GUI by "Alt + F7", it brings me a black screen. and I can do nothing then.
I want for several minutes, and I am not patient one so I reset my computer :-)

it seems that there is no problem with these kind of switches when the GL Desktop is disabled.

Anyone has the same experience? any idea?I'm getting that with beryl occasionally.

Disable your GL desktop before switching.

---

### Post by deuce868 on 2006-10-27
Thanks for the tutorial, quick question. 

I'm trying to figure out how to get this to work with a smp situation. When I went through the tutorial it installed during the initial dist-upgrade:
ii  linux-restricted-modules-2.6.17-10-386     2.6.17.5-12~amaranth 

It seemed to have put in the -386 kernel where I have a dual core and would like to use -generic. When I boot to the -generic kernel in grub I get:
"Error API mismatch: the nvidia kernel module has the version 1.0-8776, but this module has the version 1.0-9625"

I am assuming this is because I have:
linux-restricted-modules-2.6.17-10-generic 2.6.17.6-1

Do I need to do some pinning or something to get the restricted modules for the -generic kernel from your repo instead?

Thanks for any help. I'm loving the sexy graphics, but missing my second cpu.

---

### Post by Scraplab on 2006-10-28
First of all... thanks a lot for this guide!

I've got it up and running, and on the whole it seems to be quite happy. However, I seem to get quite a lot of slow down when moving windows with a few things loaded, and a lot of CPU spikes at rather strange times (ie, when nothing is being changed on screen). I had a bash at playing with the vsync and refresh rate settings, but I don't think it's that.

It doesn't do it when GL Desktop is off.

My machine should be up to spec: 2.53Ghz P4, 1Gb RAM, 256Mb 6800GT.

Any suggestions? Keep up the great work!

---

### Post by fsman on 2006-10-29
each time i reboot the "compiz-tray-icon" entry is removed from the startup programs list - so I loose compiz.

when i re-add it, it works on the first reboot and is disappears again.

any ideas what could be wrong?

---

### Post by harrisxml on 2006-10-30
When I attempt to start GL I get a white screen.  I can do nothing after that.  Using "Ctrl + alt + backspace" gets me up and running again, but I'd sort of like to use this since I installed it...

---

### Post by ekerazha on 2006-10-30
I followed this howto, however I can't see windows border and the workspace switching doesn't work (so no cube-effect).

---

### Post by deuce868 on 2006-10-30
> **fsman said:**
> each time i reboot the "compiz-tray-icon" entry is removed from the startup programs list - so I loose compiz.

when i re-add it, it works on the first reboot and is disappears again.

any ideas what could be wrong?

I get the exact same problem when placing it as a startup item in the gnome session admin tool. I guess there must be a better place to put the shortcut, although I'm not sure where to put it that it will get executed only after login to gnome.

---

### Post by tanari on 2006-10-30
Thank YOU  so much!!!!!!!!!!

3D acceleration works!

But some function not work:
water, rain and zoom :(


Can I setup more effects?

P.S.
Why sometimes windows turn to grayscale? (realy cool, but how to control this effect)

---

### Post by harrisxml on 2006-10-30
Does anyone know how to fix the "white screen" error?  I've read every post in this thread and nothing has fixed my problem.

---

### Post by jonasan on 2006-10-30
Beautiful Forum Guide got my GL Desktop up and running, except..

> **mthaddon said:**
> Still can't seem to get the water or zoom plugins working, which I think may be related to the fact that the "Windows" key doesn't work. This used to be an old issue with XGL/Compiz for NVidia. Is this still the case, or do I just have some crud somewhere that is disabling my Windows key (and if so, how do I get rid of that?)

> **tanari said:**
> But some function not work:
water, rain and zoom :(

Can I setup more effects?

OK well my problem is slightly different, my <super> key does work and so does the zoom, <super>scroll Up/Down. But Im still missing the water and rain, both obviously very important..

Faithfully

---

### Post by fsman on 2006-10-31
> **fsman said:**
> each time i reboot the "compiz-tray-icon" entry is removed from the startup programs list - so I loose compiz.

when i re-add it, it works on the first reboot and is disappears again.

any ideas what could be wrong?

Fixed it.

The first post is a bit misleading.
add "compiz --replace --use-cow gconf" to the startup programs (system->preferences->session) - thats it

---

### Post by jonasan on 2006-10-31
I have a couple problems that have developed. Firstly I added 

compiz --replace --use-cow gconf

i)to my sessions and it does work, but it loads windows without there borders. If I click enable/Disable GL a few times the windows borders magically reappear.

ii)The Icon is never in the System Tray, so I have to open it from the System->Preference Menu.

iii)following a recent update one of the window tabs in Gnome Compiz Preferences has disappeared.

iv)Er no water effects aswell

Help on any of this would be much appreciated

Regards

---

### Post by el_itur on 2006-11-01
My things:

Compiz only runs from "preferences>GL Desktop", the script in command lind does nothing but showing errors.

edited: disableng sync-to-vblank and detect frame rate resolved the issue with virtual desktops, but still I feel a little framedrops when I do anything, even typing this message is a little laggy. What can I do for reporting this bug? Nvidia - FX 5200 here

---

### Post by jonasan on 2006-11-02
> **jonasan said:**
> I have a couple problems that have developed. Firstly I added 

compiz --replace --use-cow gconf

i)to my sessions and it does work, but it loads windows without there borders. If I click enable/Disable GL a few times the windows borders magically reappear.

ii)The Icon is never in the System Tray, so I have to open it from the System->Preference Menu.

iii)following a recent update one of the window tabs in Gnome Compiz Preferences has disappeared.

iv)Er no water effects aswell

Help on any of this would be much appreciated

Regards

A recent compiz update has fixed points (i) and (iii) 

point (ii) was easy enough just manually added a new icon to the panel

still no water effects though??

---

### Post by tom56 on 2006-11-04
I have fallen at the first hurdle. Synaptic is complaing that it needs the equivalent nvidia-kernel package.

---

### Post by ekerazha on 2006-11-04
**-- Fix for "I don't see any window border and titlebar" --**

Add "gtk-window-decorator &#8211;sm-disable" to Sessions > Startup programs

**-- Workaround for "compiz-tray-icon flies away from Startup programs" --**

Open a terminal:
```
sudo gedit /usr/bin/ctistart
```

Write in:
```
#!/bin/bash
compiz-tray-icon
```
Save and close.

From the terminal:
```
sudo chmod 755 /usr/bin/ctistart
```

Add "ctistart" to Sessions > Startup programs

**-- Workaround for "workspaces switching doesn't work" --**
Right-click on compiz tray icon, Preferences > Workspaces
Click on "plane and slide" and if you want click again on "cube and rotation" (this is just to reset the setting... and it will work).

:)

---

### Post by janbockaert on 2006-11-04
is it safe to upgrade linux-restricted-modules after beryl installation?

Edgy is asking me to do an distribution upgrade, but i guess all he want is to install an update from the nvidia driver. I guess i should stay away from this update?

Jan

---

### Post by jamesford on 2006-11-04
it ****** up my beryl at least, and im unable to get it back

---

### Post by Magiczero on 2006-11-04
hi

i was hoping i would find something like this to fix my issue soon but when i try it i get this

[QUOTE][ tanner@tanner-desktop:~$ udo apt-get update
bash: udo: command not found
tanner@tanner-desktop:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libggi2 mplayer
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
tanner@tanner-desktop:~$ sudo apt-get install gnome-compiz-manager compiz-freedesktop compiz-freedesktop-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-compiz-manager
tanner@tanner-desktop:~$ 






/QUOTE]

---

### Post by Magiczero on 2006-11-04
hi

i was hoping i would find something like this to fix my issue soon but when i try it i get this

[QUOTE][ tanner@tanner-desktop:~$ udo apt-get update
bash: udo: command not found
tanner@tanner-desktop:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libggi2 mplayer
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
tanner@tanner-desktop:~$ sudo apt-get install gnome-compiz-manager compiz-freedesktop compiz-freedesktop-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-compiz-manager
tanner@tanner-desktop:~$ 






/QUOTE]

Can anyone help here?

---

### Post by Sinisterff on 2006-11-04
> **Magiczero said:**
> 
[ tanner@tanner-desktop:~$ udo apt-get update
bash: udo: command not found
Can anyone help here?

It should be "sudo apt-get update", that's why it isn't reading the packages.

And then i'm gonna ask, can some one help me here, when i try to install the new version of the nvidia drivers, Synaptic says that it needs nvidia-kernel, but it's not there.

---

### Post by Beire on 2006-11-05
yes something has gone wrong with some new updates.

---

### Post by fsman on 2006-11-06
Looks like the nvidia beta repo in the guide isn't updated. So the edgy security update is causing a conflict in update manager.
"deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm"

I've swapped to Nvidia beta repo as per this thread
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)

Commented out Aamaranth's repos and added

## aiglx cvs
deb [http://albertomilone.com/drivers/unstable/edgy/32bit](http://albertomilone.com/drivers/unstable/edgy/32bit) binary/
## deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm
## deb-src [http://amaranth.selfip.com/](http://amaranth.selfip.com/) edgy lrm
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy .

Looks like these are being updated in line with the ubuntu updates.
Perhaps the guide should be updated?

---

### Post by Sinisterff on 2006-11-06
> **fsman said:**
> Looks like the nvidia beta repo in the guide isn't updated. So the edgy security update is causing a conflict in update manager.
"deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm"

I've swapped to Nvidia beta repo as per this thread
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)

Commented out Aamaranth's repos and added

## aiglx cvs
deb [http://albertomilone.com/drivers/unstable/edgy/32bit](http://albertomilone.com/drivers/unstable/edgy/32bit) binary/
## deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm
## deb-src [http://amaranth.selfip.com/](http://amaranth.selfip.com/) edgy lrm
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy .

Looks like these are being updated in line with the ubuntu updates.
Perhaps the guide should be updated?

Thanks!, now works perfectly, but i think it has very few options to theme and plugins, i'm going to test the speed of Beryl and decide after testing both. Again thanks for the repositories :D

---

### Post by canadianwriterman on 2006-11-07
Have installed Compiz using this thread. Everything looks fine. I get the tray icon and  have enabled the GL Desktop and set preferences. Only thing that doesn't seem to work is the workspace switcher and the cube. I have 4 workspaces and they are set in the Compiz configuration utility, but I can switch between them or rotate the cube. Any suggestions?

---

### Post by canadianwriterman on 2006-11-07
Got everything working okay now by fiddling with the settings. Only thing I can figure out is how to flip the cube so I can see the top. It will only flip horizontally, and only when I move the mouse to the side. I can't "grab" the cube and rotate it in all directions.

---

### Post by canadianwriterman on 2006-11-07
Fixed.

---

### Post by tudsy on 2006-11-09
Using this thread I got things up and running on Edgy lickety split! Thanks. 

I've installed kubuntu-desktop, what needs to be done to get the compiz working in kde as well?

---

### Post by ser1alsn1per on 2006-11-09
hi I just scanned over this site so why dont you need to install xgl? 

will it work on ati  without xgl or agilx

---

### Post by frooby on 2006-11-09
I am still having problems despite all the above.  I like Xgl/Compiz on Edgy, I can run it at home, but it will not run so far at work.
I have tried many different ways to install Xgl on a fresh Edgy and get either no window borders or a white screen.
The machine is a dual PIII running "2.6.17-10-generic #2 SMP"
Graphics Card is NVIDIA GeForce MX4000
I have the Nvidia driver running, :/proc/driver/nvidia/agp/status shows:
Status:          Enabled
Driver:          AGPGART
AGP Rate:        2x
Fast Writes:     Disabled
SBA:             Enabled

But glxinfo reports:
name of display: :0.0
display: :0  screen: 0
direct rendering: No

Can anyone suggest where to go next?

Many thanks

---

### Post by janbockaert on 2006-11-09
Xgl is an x-server, that is going to replace x.org in the future (according to the xgl developers) Aiglx is a part of the x.org server that comes with edgy. Both Aiglx and xgl support compiz & beryl, the windowmanagers that bring you the actual eyecandy. So, in order to have compiz eyecandy on your desktop, you do not need xgl, as long as your gpu driver supports it. Nvidia, Intell and the opensource ati drivers support aiglx on certain cards. If your card doesn't support aiglx, you can install Xgl, but for the moment, xgl still needs x.org to work. 

When compiz first arrived last year, Xgl was the only way to get it working. Today, Aiglx is a cleaner way to get a 3d desktop, but in the end, you can't tell if your wobly windows are renderd with xgl or aiglx.

---

### Post by Jongi on 2006-11-09
Is there anyone able to provide Kubuntu specific differences?

---

### Post by blunden on 2006-11-09
So let me get this straight. You can't theme this version of Compiz?

If you can, how?

I also have trouble playing movie clips with VLC when using this Compiz version. The clips I tried were xvid. I only get a blank screen most of the time. If I move the window the image might stay visible less than a second.

---

### Post by drug on 2006-11-09
Does this work with AMD64 architecture?
The repos don't seem to have the 64 bit packages.
My attempt at installing the 386 debs by force-architecture resulted in a hard crash next time that compiz was loaded.](*,) 
Any one running this on AMD64?
Unni

---

### Post by Neophile on 2006-11-10
I have tried to install both compiz 0.3.3 but I have a problem. After a while, my screen will be populated by small windows of all the running applications (including panel applets, etc..).

Any suggestions?

My set up is edgy with nvidia 9629. This is the important bits of my xorg.conf:

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXXRootClipping" "true"
    Option         "XAANoOffscreenPixmaps" "true"
    Option         "NoLogo"
    Option         "UseEDID" "False"
    Option         "UseEDIDFreqs" "False"
    Option         "ModeValidation" "NoEdidModes"
    ...

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by skirkpatrick on 2006-11-10
It was fun to play with and I did enjoy the fact that the desktop seemed snappier.  However, until gdesklets and gdeskcal work correctly, I'm leaving it turned off but will leave it installed to play around.  The other problem is that you can't VNC into a machine running Beryl.

---

### Post by blunden on 2006-11-10
I fixed the vlc problem by selecting X11 Video Output module. Now it works perfect with transparacy, between multiple desktops etc. I also tryed mplayer which seems to work aout of the box.

My question about themes still stands though. Is it possible now? If not, will it be in a coming version?

---

### Post by RAOF on 2006-11-13
> **blunden said:**
> I fixed the vlc problem by selecting X11 Video Output module. Now it works perfect with transparacy, between multiple desktops etc. I also tryed mplayer which seems to work aout of the box.

My question about themes still stands though. Is it possible now? If not, will it be in a coming version?

Current compiz versions use the metacity theme, and have done for a couple of weeks.  You can theme it through System->Preferences->Themes

---

### Post by xcaos on 2006-11-13
Hi,

I've installed compiz using the howto described on this post. But every time that I try to run compiz (GL Desktop) the top bar dispears (yes I have added the gtk-window-decorator -sm-disable to the Sessions - Startup Prog). I also can not see the compiz cube on the bottom right corner

Any help would be extremely apreciated

thanks in advance

---

### Post by jornahow on 2006-11-16
> **canadianwriterman said:**
> Fixed.

Having had the same problem, it would be helpful if you explained what you did to fix it, instead of just posting "Fixed".

jornahow

---

### Post by justinjstark on 2006-11-17
I am getting no window borders what-so-ever and cannot move or focus any windows until I restart metacity.  Any ideas?

---

### Post by benndamann33 on 2006-11-17
I'm having a couple minor problems with beryl but all and all don't think it's nearly as unstable as you're suggesting with the heading of this post -I use compiz at work and beryl on my laptop - would say beryl is all and all a little cooler

---

### Post by 4KvRMU7Nnv on 2006-11-21
sure beryl LOOKS a little cooler but seriously, if you aren't expierencing any stability issues with it than you have the most amazing computer ever or soemthing.  Beryl only started correctly like half the time for me.  This works amazingly well though, hasn't failed once!

---

### Post by johan_lunds on 2006-11-22
Beginning of guide should be modified. This repository...
```
deb http://gandalfn.club.fr/ubuntu edgy .
```
... needs a GPG key. Run this command after adding the repository in source.list:
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x483170E9; gpg --export -a 0x483170E9 | sudo apt-key add -
```

More info: [http://gandalfn.wordpress.com/compiz-repository/](http://gandalfn.wordpress.com/compiz-repository/) (**IMPORTANT:** commands misspelled in blog-entry, can't just cut and paste, because of Wordpress' formatting)

**ANOTHER THING:** I don't think it works to just add a dot in the end of this line:
```
deb http://gandalfn.club.fr/ubuntu edgy .
```
I think you have to choose between stable and dev. I chose stable, but I don't really know.

---

### Post by kimro on 2006-11-24
New version of Compiz is out [http://gandalfn.wordpress.com/2006/11/22/compiz-034-is-out-edgy-repos-change]("http://gandalfn.wordpress.com/2006/11/22/compiz-034-is-out-edgy-repos-change")

---

### Post by stoffe on 2006-11-26
> **blaksaga said:**
> I am getting no window borders what-so-ever and cannot move or focus any windows until I restart metacity.  Any ideas?

Did you try that "test code" in the beginning (it doesn't seem to work) or did you try the compiz-tray-icon? The later worked for me, while the former did something similar as for you.

Also, wow! I've been playing a little with Beryl, but quickly getting fed up will all the crazy stuff happening and the bazillion unexplained menu choices, and had no high hopes for this, but... wow! Mostly useful stuff, modest bling, simple settings... and this is just a developers beta. Awesome. I think Beryl has its place too, and I'm happy that those who wants much and more get what they want, but it seems clear at least right now that Compiz is going to be the usable one, and triple so for a GNOME desktop.

---

### Post by finwe on 2006-11-26
> **blaksaga said:**
> I am getting no window borders what-so-ever and cannot move or focus any windows until I restart metacity.  Any ideas?

> **stoffe said:**
> Did you try that "test code" in the beginning (it doesn't seem to work) or did you try the compiz-tray-icon? The later worked for me, while the former did something similar as for you.


I'm having the same problem as blaksaga and when trying both ways that stoffe describes I end up with no window borders. Any further suggestions?

---

### Post by justinjstark on 2006-11-26
> **finwe said:**
> I'm having the same problem as blaksaga and when trying both ways that stoffe describes I end up with no window borders. Any further suggestions?

When I tried running compiz from the terminal I had this problem.  But using the launcher System->Preferences->GLDesktop works fine for me.

---

### Post by finwe on 2006-11-27
> **blaksaga said:**
> When I tried running compiz from the terminal I had this problem.  But using the launcher System->Preferences->GLDesktop works fine for me.

Okay, I wonder why the same error occurs when using GLDesktop. Maybe it has to do with my graphics card, Geforce2 MX 400, which is quite old..

---

### Post by BigJeep on 2006-11-29
Thanks for the HOWTO, it took a little tweaking to get working on my laptop but it works now.

---

### Post by corefile on 2006-11-29
When I add the repo in the derections, I get the following when I do a apt-get update

"Failed to fetch [http://amaranth.selfip.com/dists/edgy/lrm/binary-i386/Packages.gz](http://amaranth.selfip.com/dists/edgy/lrm/binary-i386/Packages.gz) 404 Not Found
Reading package lists... Done"

Looks like there is an issue with the lrm repo

Is this working for others?

---

### Post by corefile on 2006-11-30
I just realized with this method I loose my dual core proc, since this method replaces with a i386 kernel, I couldn't get this to work with the generic(smp support) kernel.

---

### Post by BigJeep on 2006-11-30
> **corefile said:**
> I just realized with this method I loose my dual core proc, since this method replaces with a i386 kernel, I couldn't get this to work with the generic(smp support) kernel.

rather than getting the nvidia driver from that repo, just download it straight from the nvidia site.  I got my laptop running compiz and the latest nvidia driver with the generic kernel.

---

### Post by MikeeAMD64 on 2006-12-04
Hello,

I have been toying around with XGL/Compiz on the Live CD for AMD64 Edgy and Dapper for a while now, and I have not been successful with any of the tutorials out there.  My problem, is that I lose the window frames.  I have no idea why I am having so many problems trying to get this to work.

I believe my problem lies with gnome-window-decorator.  For some reason when I run the following command on the front page of this thread:

```
gnome-window-decorator & compiz --replace --use-cow gconf
```

This is the message I receive:
```

[1] 8579
bash: gnome-window-decorator: command not found
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0
[1]+  Exit 127                gnome-window-decorator

```

I have tried to install gnome-window-decorator, but the package does not exist.

I appreciate any and all help I can get.  I want to play around with all the fancy visuals REALLY bad.  I want to make sure that I can get it working on the Live CD before I install it, b/c if it works on the Live CD, it will work when I install it.

Thank You.

---

### Post by shanepardue on 2006-12-04
> **scotty2hott2k said:**
> if anyone is getting tearing, i seemed to fix it by opening up gconf-editor then going into programs->compiz->screen0 (not might not be exact) then unticking autodetect refresh rate and setting my own refresh rate.
THANK YOU SO MUCH!!! I had been posting about this very problem and no one could help me! I'm so glad I found this post!!!

---

### Post by RAOF on 2006-12-04
> **MikeeAMD64 said:**
> ...
```
gnome-window-decorator & compiz --replace --use-cow gconf
```

This is the message I receive:
```

[1] 8579
bash: gnome-window-decorator: command not found
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0
[1]+  Exit 127                gnome-window-decorator

```

...

There are two problems there (and a third comment to be made).  First, gnome-window-decorator is now called **gtk**-window-decorator; the instructions on the first page are out of date.

Second, "compiz: GLX_EXT_texture_from_pixmap is missing" line means that you haven't got XGL set up correctly.  You need to do more than just install the xserver-xgl package :).

Finally, a much better way of actually enabling compiz than from the command line is to install the **gnome-compiz-manager** package (from Gandalfn's repository, or my AMD64 mirror), then going System->Preferences->GL Desktop, and hitting the button marked "Enable GL Desktop" :)

---

### Post by beefcurry on 2006-12-05
When i try compiz --replace --use-cow gconf i would get the error:

compiz: No composite extension.

When i try to use gnome-compiz-manager no options are saved, which leads me to believe this is because the --replace funtion did not work. why way to solve this?

---

### Post by beefcurry on 2006-12-05
ah stupid me, i had not have the composite extension enabled in xorg.conf, now thats fixed, but now i have no boarders when compiz is enabled. Which i see quite alot of people have this problem. Any suggestions?

---

### Post by MikeeAMD64 on 2006-12-05
> **RAOF said:**
> 
Second, "compiz: GLX_EXT_texture_from_pixmap is missing" line means that you haven't got XGL set up correctly.  You need to do more than just install the xserver-xgl package :).


Well, what exactly do I need to do?  I installed the drivers and I ran the nvidia-xconfig.


> **RAOF said:**
> 
Finally, a much better way of actually enabling compiz than from the command line is to install the **gnome-compiz-manager** package (from Gandalfn's repository, or my AMD64 mirror), then going System->Preferences->GL Desktop, and hitting the button marked "Enable GL Desktop" :)
Can you post the repository and GPG key, b/c I have been looking all over and I can't find them.  Also, most of the repositories that are hosing XGL/Compiz stuff don't work anymore.

Does anybody honestly know when XGL/AGLIX/Compiz will be completed, and when Ubuntu will finally get them working without having to manually install it?

---

### Post by RAOF on 2006-12-05
> **MikeeAMD64 said:**
> ...

Does anybody honestly know when XGL/AGLIX/Compiz will be completed, and when Ubuntu will finally get them working without having to manually install it?

It works right now in Feisty :).

Rather than trying to get XGL to work, I'd suggest getting the newer nVidia drivers - search for the tselliot's Envy script, or just visit [http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

Then you don't need to wory about setting up XGL at all.

Links to my repository are right there in my sig :).

---

### Post by Amaranth on 2006-12-05
Feisty has the 9629 nvidia driver and has compiz in universe so all you have to do it a little change in xorg.conf, install desktop-effects, and go. Beryl will probably be in fesity universe when the 0.1.3 release comes out.

---

### Post by MikeeAMD64 on 2006-12-05
Wait, so Feisty already has it working with all the effects turned on out of the box?

---

### Post by RAOF on 2006-12-05
> **MikeeAMD64 said:**
> Wait, so Feisty already has it working with all the effects turned on out of the box?

Not quite.  But it's **installable** out of the box.  And if you have a {Intel, nVidia, (sufficiently old) ATI} graphics card, you won't need to do anything but install it.

Hopefully Gandalfn's gnome-compiz-manager packages will be accepted into Feisty's Universe soon, then it will be easily configurable out of the box, too :).

It's also a goal of Feisty to have one of Compiz/Beryl working out of the box, wherever possible.

---

### Post by Mithrilhall on 2006-12-05
Well..I got it working actually. I had to change the section titled 'Extensions' in xorg.conf. I changed:

Option "Composite" "Disable" to
Option "Composite" "Enable".



Thanks.



Okay...When I run beryl-manager everything disappears other than the mouse cursor.

When I run 'beryl' I get:

```

eric@debian:/etc/init.d$ beryl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension
eric@debian:/etc/init.d$

```

How do I check what Nvidia driver I'm using?

---

### Post by MikeeAMD64 on 2006-12-05
Feisty is not yet available. So, what exactly should I do?  
The thing is, next semester, I have an Operating Systems course, and we do a lot with Linux.  I have been using Linux on and off for a while so I'm quite comfortable with it.  Now, since I have to install Linux anyway, I want to go ALL OUT!  I just recently built this computer, and I want to use the hardware to its fullest.  So, getting XGL/Compiz or whatever to work is a huge priority for me.

---

### Post by RAOF on 2006-12-05
You have two (ok, three, but one of them isn't very good :)) options:
1) a) Install the new (9629) nVidia drivers, using this guide: [http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

b) run ```
sudo nvidia-xconfig --add-argb-glx-visuals --allow-glx-with-composite --composite --damage-events --disable-glx-root-clipping
```

c) Then, get the **compiz-freedesktop**, **gnome-compiz-manager**, **compiz-freedesktop-extra**, and **gnome-compiz-manager-extra** packages from my repository (or, better, one of the mirrors).

d) Go System->Preferences->GL Desktop, and go *crazy!*.

2) Upgrade to Feisty and skip part a) above :).

3) (not so good) Install and set up xserver-xgl.

---

### Post by klato on 2006-12-06
Not working over here...does anyone know a sure way to get Compiz running? I can get Beryl running no problem, but this Compiz is confusing the HELL out of me (checked on here, compiz forums, and even the instructions at the compiz page but they seem pretty useless to me)](*,)

Edit: working

---

### Post by MikeeAMD64 on 2006-12-06
For reference, ROAF's repo link is:  deb [http://raof.dyndns.org/falcon](http://raof.dyndns.org/falcon) edgy  eyecandy

The GPG key is listed in the mirrors listed in his sig.

---

### Post by MikeeAMD64 on 2006-12-06
> **RAOF said:**
> You have two (ok, three, but one of them isn't very good :)) options:
1) a) Install the new (9629) nVidia drivers, using this guide: [http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)

b) run ```
sudo nvidia-xconfig --add-argb-glx-visuals --allow-glx-with-composite --composite --damage-events --disable-glx-root-clipping
```

c) Then, get the **compiz-freedesktop**, **gnome-compiz-manager**, **compiz-freedesktop-extra**, and **gnome-compiz-manager-extra** packages from my repository (or, better, one of the mirrors).

d) Go System->Preferences->GL Desktop, and go *crazy!*.

2) Upgrade to Feisty and skip part a) above :).


3) (not so good) Install and set up xserver-xgl.

YES!!! IT WORKS!!

Thank you so much!

EDIT: I couldn't find the gnome-compiz-manager-extra.  What does that package do?  For some reason, I wasn't able to use the cube.  Also, I remember when I was trying to get this working before, there was a program that had a bunch of checkboxes, and with it, you can choose exactly the keyboard shortcuts and effects you want to turn on and off.  Where is that?

Thank you!

---

### Post by MikeeAMD64 on 2006-12-09
Ok, I decided to install Ubuntu, but I am now having problems with the Nvidia driver.
For some reason, when I restart my system, it cannot load X.  It gives me an awkward error.  It mentions something about mismatched API's.
To fix it, I have to reinstall the nvidia driver **EVERYTIME** I restart my computer in order to log in.
This is very bizzare.  What is going on?

[EDIT]Ok, I figured it out.  I needed to go into: /etc/default/linux-restricted-modules-common, and I where it says:
```
DISABLED_MODULES=""
```
I needed to modify it with:
```
DISABLED_MODULES="nv"
```

---

### Post by MikeeAMD64 on 2006-12-09
Ok, I should have mentioned that I am now using 32-bit, and the compiz free-desktop ones no longer work.  

What am I supposed to do?

EDIT: Ok, I'm then going back to the 64 bit version.  (I installed the 32-bit version b/c I thought the issue I was having before was because of the 64-bit version)

---

### Post by RAOF on 2006-12-10
> **MikeeAMD64 said:**
> Ok, I should have mentioned that I am now using 32-bit, and the compiz free-desktop ones no longer work.  
...

If you're talking about my repositories, then yes.  They don't contain i386 packages - gandalfn's own repositories handle that.

My repositories are focused at the poor, neglected AMD64 users :)

---

### Post by MikeeAMD64 on 2006-12-10
Ok, I am just not a fan of GNOME.  I tried to install KDE, and messed everything up.  So, I have Kubuntu running right now, but I have no clue how to get compiz running, since most of the packages are gnome packages.

What do I do now?

EDIT:  Actually, Kubuntu is just WAY too buggy.  And, I don't know WHAT happened to KDE, but it has gotten way too bloated and crappy.  I'm just going to go back to Gnome.

RAOF, is your repo working?  Before, while I was in KDE, I tried to use it and it kept timing out.

---

### Post by RAOF on 2006-12-10
> **MikeeAMD64 said:**
> ...
EDIT:  Actually, Kubuntu is just WAY too buggy.  And, I don't know WHAT happened to KDE, but it has gotten way too bloated and crappy.  I'm just going to go back to Gnome.

RAOF, is your repo working?  Before, while I was in KDE, I tried to use it and it kept timing out.

Excellent.  Another follower of the One True Gnome :p.

My repository **should** be working.  As long as you're using the mirrors, they should be up 24/7.  The main link goes to my home computer, which is up roughly 12/7 :).

---

### Post by sanone on 2006-12-11
> **johan_lunds said:**
> Beginning of guide should be modified. This repository...
```
deb http://gandalfn.club.fr/ubuntu edgy .
```
... needs a GPG key. Run this command after adding the repository in source.list:
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x483170E9; gpg --export -a 0x483170E9 | sudo apt-key add -
```

More info: [http://gandalfn.wordpress.com/compiz-repository/](http://gandalfn.wordpress.com/compiz-repository/) (**IMPORTANT:** commands misspelled in blog-entry, can't just cut and paste, because of Wordpress' formatting)

**ANOTHER THING:** I don't think it works to just add a dot in the end of this line:
```
deb http://gandalfn.club.fr/ubuntu edgy .
```
I think you have to choose between stable and dev. I chose stable, but I don't really know.

Thanks for pointing this out... I had it working but removed it due buddy drivers. Now I have it working again ;)
```
deb http://gandalfn.club.fr/ubuntu edgy stable
```

@topic starter: please keep your starters post up-to-date... saves a lot of people reading 16+ pages!

---

### Post by MikeeAMD64 on 2006-12-11
I can't get the cube to work.

Also, it's not remembering the amount of workspaces I set whenever I log back in.

---

### Post by Skerit on 2006-12-12
How about updating the original message, or deleting it from the "One thread to rule"... list because everything about it doesn't work anymore...

---

### Post by MikeeAMD64 on 2006-12-15
Ok, for some reason, my computer keeps freezing when leaving the Xserver.  Whenever I try to go to a terminal (CTRL + ALT + F1) or just shutting down, it just freezes and becomes completely unresponsive.  I have to push the power button or reset button on my computer to shut down.

I don't understand why it would all of a sudden do this.  I didn't update anything or remove any needed app.

EDIT:  Fixed.  I followed the instructions listed here: [http://ubuntuforums.org/showthread.php?t=318142&highlight=Freeze+on+shutdown](http://ubuntuforums.org/showthread.php?t=318142&highlight=Freeze+on+shutdown)

In /etc/gdm/gdm.conf, on line 96, make #AlwaysRestartServer=false to AlwaysRestartServer=true

---

### Post by Jott on 2006-12-21
Hi RAOF,

The link to your repos in your sig keeps timing out -

could you post your mirrors?

Thanks

EDIT: NEVERMIND

Sorry, just saw the previous post with your mirrors listed.  Didn't pay enough attention the first time through.

---

### Post by ghepardo on 2006-12-21
THe repositories does not work more. Someone can update them tnx!?

---

### Post by Grog140 on 2006-12-22
Its working but I am getting no window decorations.

I have no idea how to get them to work either. Anyone else know?

---

### Post by MikeeAMD64 on 2006-12-22
That was my biggest problem at first.  I tried ROAF's instructions on the previous 2 pages when I began to post, and that worked for me.

---

### Post by MeathooK427 on 2006-12-22
I installed Compiz with the guide found here: [http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy)

and tried revising a little with the comments on this thread.

The installation seemed to go flawlessly, didn't get any errors

However, I can't find compiz anywhere, not in the taskbar, applications, nowhere!

Whenever I type compiz in terminal, it gives me:

compiz: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz: No manageable screens found on display :0.0

What'd I do wrong???

Also, I'm in an nvidia 7800 gs, and I recently installed the latest nvidia drivers.

---

### Post by Amaranth on 2006-12-22
```
compiz --use-cow --replace gconf
```

---

### Post by BoneyOne on 2006-12-25
I'm on edgy and trying Compiz (0.3.4 dev) with my lappy (nvidia 6200). It install's just fine, I run it from either the icon, or terminal all borders disapear. I've read through all 19 pages and still haven't been able to get this to work.

EDIT: I'm on the 9746 drivers

---

### Post by MikeeAMD64 on 2007-01-19
Has there been any updates to the compiz-freedesktop packages?

When I try doing sudo apt-get install update, it says that that it won't touch compiz.  I then try sudo apt-get install compiz-freedesktop, it says that it wants to remove the free-desktop packages, and it wants to install regular compiz over it.

I really don't want to touch anything, since it's working for me, but it would be nice to see an update to some of the bugs.

---

### Post by RAOF on 2007-01-21
The "compiz-freedesktop" packages have been renamed just "compiz".  Partially because there were no other compiz packages (just beryl packages), so the freedesktop qualifier was unnecessary, and partially to fix the naming for the package in Feisty's Universe repository.

Now people can apt-get install compiz in Feisty and not get an ancient, pre-beryl Quinn version of compiz :).

---

### Post by MikeeAMD64 on 2007-01-21
Ok, problem.  I did "apt-get install compiz", and now I no longer have the window decorations anymore!

BTW, the US repo doesn't work anymore.  I also had an error with a freedeskop package when using the DE mirror, so I commented it out of the sources.list from the sources.list.

EDIT:  I tried using the "compiz --use-cow --replace gconf" command (I have to do that everytime), and that seemed to work, but I noticed that I'm missing many effects.  Before, I was able to set the type of effects I wanted to put on the windows, and now I can't.  The other MAJOR problem is that I can no longer leave the X-server without my system freezing.

EDIT:  I fixed the freezing problems by:
```
sudo gedit /etc/gdm/gdm.conf
```

Then, I set:
```
AlwaysRestartServer=false
```

---

### Post by RAOF on 2007-01-22
Hm, you might also want the compiz-gnome and compiz-extra packages, and gnome-compiz-manager(& -extra).

But my compiz is a little bit munted at the moment.  Given that recent compiz is now available in Feisty's Universe, I'll start rebuilding the (slightly) older (and more stable, hopefully), Edgy packages that Gandalfn does.

---

### Post by MikeeAMD64 on 2007-01-22
I tried to install the extra packages, but it gave me a missing dependency error.  EDIT:  It's missing compiz-extra.

Do the packages on the Feisty repos work?

EDIT:  Should I try building Compiz from the instructions on this page: [http://go-compiz.org/index.php?title=Compiling](http://go-compiz.org/index.php?title=Compiling)  
I have never had any success with building packages before, so I'm a little reluctant of doing it.  Or, should I wait until you get the packages properly working?

EDIT:  Tried to compile compiz-extra, and it didn't work like usual.  I'm getting some gay error: "configure: error: C compiler cannot create executables".  I have g++ and libc6-dev installed.  I can't think of anything else that would cause this issue.

---

### Post by chuvisco on 2007-01-22
> **RAOF said:**
> Hm, you might also want the compiz-gnome and compiz-extra packages, and gnome-compiz-manager(& -extra).

But my compiz is a little bit munted at the moment.  Given that recent compiz is now available in Feisty's Universe, I'll start rebuilding the (slightly) older (and more stable, hopefully), Edgy packages that Gandalfn does.

First of all, thank you for providing the AMD64 freedesktop packages--they are working great.  I look forward to the updated packages when you are able to get to it.

---

### Post by MikeeAMD64 on 2007-01-22
As it turns out, I can't compile any software at all.  It appears my libc.so.6 file is messed up somehow.  I keep getting:
```
/lib/libc.so.6: file not recognized: File format not recognized
```

That was also in the config.log.

---

### Post by MikeeAMD64 on 2007-01-23
I figured out why I was having compilation problems.  I tried to install compiz off of the Feisty repo, and it overwrote some existing packages.  And, since the feisty packages are newer than the edgy packages, I can't remove them.

I'm going to have to re-install Ubuntu, b/c everything is pretty much broken right now.

---

### Post by MikeeAMD64 on 2007-01-23
Ok, I got everything reinstalled, and I was even able to install the extra packages.  (I had to use the DE mirror)

But, I am unable to get the window decorations.  Here is the error message:

---

### Post by MikeeAMD64 on 2007-01-23
Sorry for all the posts, but I now have Compiz working.

My only problem now, is that it doesn't turn on by itself.  Also, the tray icon for GL Desktop doesn't turn on by itself either.  I'll have to take a look at that a little later.

---

### Post by MikeeAMD64 on 2007-01-24
Ok, I got it working for the most part.

The issues I am having now are where the window decorations sometimes disappear at random.

---

### Post by RAOF on 2007-01-24
> **MikeeAMD64 said:**
> Ok, I got it working for the most part.

The issues I am having now are where the window decorations sometimes disappear at random.

Any pearls of wisdom you could share?

**I** can share that the 0.3.6 gtk-window-decorator is known to be moderately unstable.  When it dies, the window decorations will disappear (or, worse, just stop responding).  Just run "killall gtk-window-decorator && gtk-window-decorator" to kill it and start it again :).

---

### Post by MikeeAMD64 on 2007-01-25
> **RAOF said:**
> Any pearls of wisdom you could share?

**I** can share that the 0.3.6 gtk-window-decorator is known to be moderately unstable.  When it dies, the window decorations will disappear (or, worse, just stop responding).  Just run "killall gtk-window-decorator && gtk-window-decorator" to kill it and start it again :).

I placed a shortcut on my desktop titled "Restart Compiz", and in it, I run:
```
compiz --replace gconf
```
So, whenever the window decorations die, I just double-click that and they come back.  I'll have to try the command you posted to see if that works better.

As for getting it working, I reinstalled Ubuntu, installed the latest Nvidia driver, upgraded my whole system, installed all the dev packages (build-essential, libc6-dev, etc.), added your repo to the list, and installed all of the compiz (not freedesktop) packages in the repo, and it worked.

---

### Post by dragnazz5.0 on 2007-02-05
well im trying to use this as a guide to install compiz but i get an error when i sudo apt-get update.  this is the error i get

Ign [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy Release.gpg                                
Ign [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy/lrm Translation-en_US                      
Ign [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy Release                                    
Ign [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy/lrm Packages                               
Err [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy/lrm Packages
  404 Not Found
Get:4 [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release.gpg [189B] 
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/. Translation-en_US  
Hit [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release
Err [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release
  
Get:5 [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release [6127B]
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/. Packages
Err [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/. Packages
  404 Not Found
Fetched 6319B in 46s (135B/s)
Failed to fetch [http://amaranth.selfip.com/dists/edgy/lrm/binary-i386/Packages.gz](http://amaranth.selfip.com/dists/edgy/lrm/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gandalfn.club.fr/ubuntu/dists/edgy/./binary-i386/Packages.gz](http://gandalfn.club.fr/ubuntu/dists/edgy/./binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBF6E0B8483170E9
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by MikeeAMD64 on 2007-02-05
^Remove those repos, and add this to your sources.list file:

```
deb http://ubuntu.moshen.de edgy eyecandy
deb-src http://ubuntu.moshen.de edgy eyecandy
```

Then: ```
sudo wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -
```

You may also want to add ROAF's repo to the list, but his is usually down.  
```
deb http://roaf.dyndns.org edgy eyecandy
deb-src http://roaf.dyndns.org edgy eyecandy
```

Good luck, you'll need it.

---

### Post by dragnazz5.0 on 2007-02-05
well now i get this error

W: GPG error: [http://ubuntu.moshen.de](http://ubuntu.moshen.de) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651
W: You may want to run apt-get update to correct these problems

nevermind...im retarded

---

### Post by tanneeru on 2007-02-17
Hi I am very new to Linux and I tried the infor given here for installing compiz..

And I get the error..like this at the end

sagar@sagar-laptop:~$ sudo apt-get update
Password:
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Get:2 [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release.gpg [189B]                          
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/. Translation-en_US                           
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Get:4 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]          
Get:5 [http://kubuntu.org](http://kubuntu.org) edgy Release.gpg [189B]                               
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US        
Get:6 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]        
Ign [http://kubuntu.org](http://kubuntu.org) edgy/main Translation-en_US                             
Get:7 [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy Release.gpg [191B]             
Ign [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Translation-en_US         
Get:8 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release.gpg [191B]                        
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Translation-en_US                      
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Ign [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy Release.gpg                                
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US             
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Get:10 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release.gpg [191B]                 
Hit [http://kubuntu.org](http://kubuntu.org) edgy Release                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Ign [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Translation-en_US         
Ign [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Translation-en_US         
Hit [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy Release                          
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release                                     
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                              
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Hit [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                     
Err [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release                                       
  
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main-edgy Translation-en_US           
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US                
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Translation-en_US                
Hit [http://kubuntu.org](http://kubuntu.org) edgy/main Packages                                      
Ign [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy/lrm Translation-en_US                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US             
Hit [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                          
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US         
Hit [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Packages                  
Hit [http://nvidia.limitless.lupine.me.uk](http://nvidia.limitless.lupine.me.uk) edgy/stable Packages                  
Get:15 [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release [6127B]                            
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                             
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages                               
Ign [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy Release                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US       
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources               
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Translation-en_US             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                 
Ign [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/. Packages                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                            
Ign [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy/lrm Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release                                   
Err [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy/. Packages                                    
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Err [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy/lrm Packages
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Fetched 6521B in 2s (3184B/s)
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/Release](http://ubuntu.beryl-project.org/dists/edgy/Release)  Unable to find expected entry  main-edgy/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://gandalfn.club.fr/ubuntu/dists/edgy/./binary-i386/Packages.gz](http://gandalfn.club.fr/ubuntu/dists/edgy/./binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://amaranth.selfip.com/dists/edgy/lrm/binary-i386/Packages.gz](http://amaranth.selfip.com/dists/edgy/lrm/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBF6E0B8483170E9
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
sagar@sagar-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sagar@sagar-laptop:~$ sudo apt-get install gnome-compiz-manager compiz-freedesktop compiz-freedesktop-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-compiz-manager
sagar@sagar-laptop:~$

---

### Post by MikeeAMD64 on 2007-02-17
I think most of those repos aren't available anymore.

---

### Post by Carrots171 on 2007-03-16
> **MikeeAMD64 said:**
> I think most of those repos aren't available anymore.

The repositories given in this HOWTO don't seem to work anymore. ](*,)  I would appreciate it if someone could tell us where we could find working repositories for Compiz/Nvidia drivers, and perhaps update this HOWTO, also.

---

### Post by EXCiD3 on 2007-08-24
Install your NVIDIA drivers using ENVY: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And use the Compiz Fusion installer script for installation: [http://ubuntuforums.org/showthread.php?t=508769&highlight=cf+installer](http://ubuntuforums.org/showthread.php?t=508769&highlight=cf+installer)

---

