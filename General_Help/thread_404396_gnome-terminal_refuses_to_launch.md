---
title: "gnome-terminal refuses to launch"
date: 2007-04-08
forum: General Help
---

### Post by Spr0k3t on 2007-04-08
I updated one of my data storage computer systems last night to feisty beta and installed the updates through the Update Manager.  Now, the terminal refuses to launch.  I try to open the terminal and the window notification area is showing "Starting Terminal", but after a few seconds it closes.  I tried going to recovery mode and performed a startx, I get the same result logged in as root user.  I looked through Launchpad to see if I could find a bug on this one, but no luck.

The only application I've installed on this system is Weechat 0.2.4 (dependancies: libncursesw5, libncursesw5-dev).  The only drivers I've installed are Atheros Hardware Access Layer and NVIDIA accelerated graphics driver.

Need some help with this one.

---

### Post by ebash on 2007-04-08
I had a similar problem with some applications that refused to start when enabling the composite extension in X.org and when using the new NVIDIA drivers.

The following bug shows some workarounds:  [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232")

The easy way to fix this is to update the X.org configuration to add the following line in the section "Screen":
```
Option "AddARGBGLXVisuals" "True"
```

You can also set the environment variable:
```
XLIB_SKIP_ARGB_VISUALS=1
```

In the mean while, if you are logged and you would like to have a terminal create a panel launcher with the following command:
```
sh -c "XLIB_SKIP_ARGB_VISUALS=1 exec gnome-terminal"
```

---

### Post by Spr0k3t on 2007-04-08
Wow!  Dead on.  This fixed the problem... poifect!

---

### Post by raydar on 2007-10-08
I'm having the same problem in Feisty UbuntuStudio.  I added the "Option" line to my xorg.conf as you suggested, as follows:

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT-0: 1600x1200_60 +0+0; CRT-0: 1600x1200 +0+0; CRT-0: 1280x1024 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

but there was no difference after an X restart or a reboot.  So I added the same line to the second of the two "Screen" sections in my xorg.conf, and still no difference after an X restart or a reboot.  (Since I couldn't get into a terminal, I used Ctrl+Alt+F5 and edited xorg.conf there.)

Seems I would've noticed this before, so I'm tempted to doubt this has been a problem ever since I installed UbuntuStudio on this box.  It's an experimental box I'm only now revisiting frequently. and I can't think what I could've done that would've caused Terminal to break (all I've changed about it is installing & uninstalling some things like vlc & mplayer to try & get video & sound to work better).

---

### Post by raydar on 2007-10-19
Upgrade to Gutsy fixed this for me.

---

### Post by raydar on 2007-10-30
Not so fast!

How fickle is the upgrade from Feisty to Gutsy:  I majorly screwed my successfully upgraded UbuntuStudio installation, the upgrade of which fixed this problem for me.  I had to reinstall the OS, but I couldn't burn a DVD of Gutsy UbuntuStudio because (1) [http://ubuntuforums.org/showthread.php?t=590487&highlight=ubuntustudio+800mb](http://ubuntuforums.org/showthread.php?t=590487&highlight=ubuntustudio+800mb) and (2) my system still suffers from [http://ubuntuforums.org/showthread.php?t=447912](http://ubuntuforums.org/showthread.php?t=447912) .

So I went back & found the Feisty UbuntuStudio DVD I had burnt while I still had a Windows partition, and installed Feisty UbuntuStudio with that.  Same disc I had used to create the installation I destroyed, in which I first had the Terminal-won't-start problem in.  But when I upgraded to Gutsy this time, it *created* the terminal-won't-start condition, as opposed to getting rid of it.

I tried ebash's solution and bam, fixed.  Many thanks! :)

But what causes this?  Is that line usually written to xorg.conf by _____, which I happened not to have run?  Like nvidia-xconfig, or something?  I did go straight to Synaptic to install the new Screens and Graphics app (displayconfig-gtk, just new enough not to have been included in the UbuntuStudio distro, according to their mailing list) this time after enabling the restricted drivers, where I think on most or all previous installations I had used nvidia-settings and nvidia-xconfig.

---

