---
title: "I killed Xfree config"
date: 2004-11-13
forum: General Help
---

### Post by Patrick on 2004-11-13
whooops,

I tryed to edit my config to get the tv out working, i restarted the computer, now i'm looking to a black screen, saying it cant find the monitor.

How can i edit the Xfree file?

( no i didnt made a backup, stupid me!! )

---

### Post by ubik on 2004-11-13
Well, just post your config file and the log file tosee if somebody can help you:
```

/etc/X11/XFree86-4
/var/log/XFree86.0.log
```

or if you want to reconfigure yourself then
```
sudo dpkg-reconfigure xserver-xfree86
```
should do the trick.

---

### Post by Patrick on 2004-11-13
Thx for your repley,

I  tryed the reconfigure, but i i dont get the change to delete the extra lines i added to the file to add tv out. 

This way i only can change the mouse and the monitor.

The error given = No monitors found.

---

### Post by candymanobh3 on 2004-11-13
If you have the liveCD, boot it up and copy the config file in /etc/X11 over your old one & that should do it. That's one of the many uses I've found for the live CD. :wink:

---

### Post by ubik on 2004-11-13
To get TV-out working you need to define two monitors (one is the TV the other for your monitor), two cards and two screen, it should give something like:
```
Section "Monitor"
   Identifier "Monitor"
   HorizSync blah-blah
   VertRefresh blah-blah
EndSection

Section "Monitor"
   Identifier "TV"
   HorizSync blah
   VertRefresh blah-blah
EndSection 
 
Section "Device"
        Identifier      "Card-0"
        Driver          "nvidia"
        Screen 0
EndSection

Section "Device"
        Driver          "nvidia"
        Identifier      "Card-1"
        Option          "TVOutFormat" "Composite" 
        Option          "TVStandard" "blah"
        Option          "ConnectedMonitor" "TV"
        Screen 1
EndSection 


Section "Screen" 
    Identifier  "Screen0"
    Device      "Card-0"
    Monitor     "Monitor"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1600x1200"
        ViewPort    0 0
    EndSubsection
EndSection

Section "Screen"
Device "Card-1"
Identifier "Screen1"
Monitor "TV"
DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "1024x768"
        EndSubSection   
EndSection 

Section "ServerLayout"

    Identifier  "Simple Layout"
        Screen 0 "Screen0"
        Screen 1 "Screen1" RightOf "Screen0"
        InputDevice "Mouse" "CorePointer"
        InputDevice "Keyboard" "CoreKeyboard"

EndSection 
```

[Here](http://forums.gentoo.org/viewtopic.php?t=122823&start=0&postdays=0&postorder=asc&highlight=nvidia+tvout)'s a howto in gentoo's forum. Hope this help.

---

### Post by HiddenWolf on 2004-11-13
And please, before you do anything to an XFree86 config, please back it up.

I just did an upgrade to hoary, and had a few old configs for Xfree lying around. I could just copy an old one over xorg.conf untill I found one that worked.
The first time ever that an xfree config file saved me pain, that is.

---

