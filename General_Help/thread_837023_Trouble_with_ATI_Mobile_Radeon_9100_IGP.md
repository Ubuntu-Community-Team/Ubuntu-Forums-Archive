---
title: "Trouble with ATI Mobile Radeon 9100 IGP"
date: 2008-06-22
forum: General Help
---

### Post by Parrothead74 on 2008-06-22
Hello. I am a BRAND NEW Linux convert, so go easy on me. I just installed Hardy on my little Toshiba A75-S206 Laptop. It has the above video graphics. I saw some cool videos of Beryl and wated to give it a go. Well, I can even turn on "Visual Effects". I've been in and out of so many forums and websites today my brain seems a bit scrambled. Apparently, this little 3D accelerated video card doesn't go 3D very well in Linux. I need some guidance to get the litle ******* working and would greatly appreciate it. Cheers. Dave

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

### Post by Parrothead74 on 2008-06-22
Piet. Thanks for the info, after I sleep a bit I'll give it a go and let you know how it works.

---

### Post by Forlong on 2008-06-22
> **Parrothead74 said:**
> Hello. I am a BRAND NEW Linux convert, so go easy on me. I just installed Hardy on my little Toshiba A75-S206 Laptop. It has the above video graphics. 
...
Well, I can even turn on "Visual Effects"
...
I need some guidance to get the litle ******* working
What do you mean exactly -- if it's working for you, what else do you expect?

Please be a little more specific.

---

### Post by Parrothead74 on 2008-06-22
Forlong. I mistyped that, sorry. Contained within my first post IS the specific problem, though I might have worded it better. 

The EXACT problem is that I cannot seem to enable 3D acceleration on my video chipset. The graphics chipset is ATI Mobile Radeon 9100 IGP, integrated motherboard graphics. The chipset is supposed to support 3D acceleration, but I'm not sensing a lot of love out there for this chipset by ATI or Ubuntu communities. 

I REALLY want to use Beryl, or some of the more eye-pleasing themes but at this time I cannot even use the simple, pre-loaded "Visual Effects" packaged with Hardy. 

I've not yet tried pietjanjaap's fix, but if I get a moment today i will. Thanks for looking into this for me. One day I will return as a sophisticated Linux user and provide help for others!

---

### Post by Forlong on 2008-06-23
Please run this before doing anything: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by prabath_fun on 2008-06-23
HI,


 I am using Ubuntu8.04 with wubi. I am trying to get 3D desktop. I tried two ways.

1. In Restricted hardware, tried to enable the display driver. It asks "xorg.fglrx-*******". I installed and rebooted. After username and password entered, screen gone white.
Then, I booted in safe mode, fixed it. But, resolution gone from 1024*768 to 800*600. So, I went again to restricted hardware and disabled it. Now it is working as with old settings, but still no 3D effect?

2. Right click on desktop -> change desktop background -> Effects. There I clicked on the options provided one by one. My screen becomes white and then come back & gives the message "cannot  enable desktop effects".


Please guide me how to get it.

Advanced Thanks

---

### Post by Rocket2DMn on 2008-06-23
Parrothead,
I'm still unclear on what your problem is.  Can you enable visual effects?  If it says Effects cannot be enabled, see this thread: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
Otherwise, please post the following:
```
lspci | grep VGA
cat /etc/X11/xorg.conf
```
Did you try to install restricted/proprietary drivers?  If so, you should not have and need to remove them since your card is too old for them.

---

### Post by Parrothead74 on 2008-06-24
Forlong and Rocket: I gave up on Hardy. I tried EVERYTHING you guys mentioned and more, it just seems that the little video card and Hardy don't get along. I used open source and proprietary drivers, and all I ended up with is a mess on my system. I know my way around a Windows or Macintosh box pretty well, but the file system in Linux is daunting for me right now.

Anyway, not being a complete wuss, I tried another approach and it worked. I simply ran a clean install of Gutsy, and it worked out of the box. Effects are now able to be ENabled, and I think I am good to go. If ya's have any patience left for me, maybe you could guide me to a thread that teaches retards like me how to get themes active.

I really like Gutsy, especially when compared to Hardy. Seems a lot more ironed out and stable. Thanks for the help. Cheers ~Dave

---

### Post by Parrothead74 on 2008-06-24
Oh, and Forlong. I ran the script for Compiz-check (I think). I navigated to /usr/bin/compiz-check and double clicked it (windows guy, right :-) I was presented with 4 options and I tried them all. The one that did the best was the one about running it in the Terminal. Well, I had to run it about 6 times to glean the info I was after as the terminal kept shutting off as soon as the full display was out. Thanks for that, though. I think it was 4 green OK's. ~Dave

---

### Post by Forlong on 2008-06-24
> **Parrothead74 said:**
> Anyway, not being a complete wuss, I tried another approach and it worked. I simply ran a clean install of Gutsy, and it worked out of the box. Effects are now able to be ENabled, and I think I am good to go.
Awesome. :)
> **Parrothead74 said:**
> If ya's have any patience left for me, maybe you could guide me to a thread that teaches retards like me how to get themes active.
There's really not much to know.
Just go to *System &#8594; Preferences &#8594; Appearance* to choose a theme.

You'll find a lot of other ones here: [http://gnome-look.org](http://gnome-look.org)
Most themes should come in a tarball (archive) and all you have to do is drag & drop it into the Appearance window to install it.
> **Parrothead74 said:**
> Oh, and Forlong. I ran the script for Compiz-check (I think). I navigated to /usr/bin/compiz-check and double clicked it (windows guy, right :-)
Even a windows guy should be able to read the manual, right? :)

Easiest way would be following the steps mentioned on the site -- all you had to do was copy & paste them into your terminal.

But it seems like you went with th deb package. Well that's even easier than on Windows.
You don't have to know where the files are on Linux. Most of the time you can just enter the name of the application into the terminal (or [Alt]+[F2]) and it wil run.

The thing with Compiz-Check is, though, that it's a terminal-only program (I made a backup GUI but it's not released yet) -- so just fire up your terminal and type ```
compiz-check
```
Easy as pie. :)

---

### Post by pixel4e on 2008-09-13
Ok I am having similar problems in Hardy with the same chipset. I tried everything, I tryed following the guides, there is always some kind of issue. I don't have the drivers listed in my restricted drvers at all. I tried EnvyNG and it completely ****** me up. The proprietary driver from the ATI website requires Xorg installed which I HAVE and it just doesn't want to continue whatever I do. Does anyone have an idea how to make this chipset work from clean install without having the restricted drivers available?

---

### Post by marktechey on 2008-09-14
In order to get the ATI Mobility 9000/9100 IGP card working in Hardy make sure the following things are true. 

First, make sure the fglrx is completely remove from your system. To do this, do the following. (In a terminal of course) 

sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

Then, again in a terminal, type the following command:

gksudo displayconfig-gtk

When it opens, click on the graphics card tab, and then click on the driver selection. Then look at the picture attached. (Choose graphic card one) Press ok.

Then go back to the screens tab. And click on the screen selection next to where it says model. See other screenshot.(Choose screen) Then click ok to select that screen.

Now press test. Screen should go a bit funky for a second, then come up with something that asks you either keep your selection or something else that I forget. Choose to keep your selection.

(Steps below are from this thread [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633))
Now, last step. Do the following in a command line.

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

It may also help to install the following.
sudo apt-get install compizconfig-settings-manager

Restart xserver by pressing ctrl + alt + backspace all at the same time. Login in and it should work! Good luck

---

### Post by AndyCinDallas on 2008-10-31
Marktechey - you are a god! :mrgreen:

Your instructions worked beautifully for me on Hardy running the same gfx card mentioned - ATI Mobility Radeon 9000 IGP :grin:

andy@laptop:~$ compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

