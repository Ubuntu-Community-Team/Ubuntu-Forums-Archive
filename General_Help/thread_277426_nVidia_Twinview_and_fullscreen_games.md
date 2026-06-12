---
title: "nVidia Twinview and fullscreen games"
date: 2006-10-14
forum: General Help
---

### Post by Knifa on 2006-10-14
Helloes.

I'm trying to run World of Warcraft using WINE with Twinview but have it only show on my main monitor, leaving the other one free for web browsing, IRC, MSN, etc but right now, when I start it in fullscreen mode, it displays right in the middle of the screen rendering it unplayable. The game itself runs fine (better than it runs in Windows, oddly enough) and it also works perfectly with only one monitor connected.

tl;dr: How do I get fullscreen games to run on one monitor rather than sitting in the middle of both monitors so I can't see anything.

Thanks!

---

### Post by CapnCook on 2006-10-14
I don't know if this will work with wine but it works for native linux games. Open the /etc/X11/xorg.conf file and scroll down to the Device section listing your video card, on the options "MetaModes" line at the screen resolution you are running add NULL as the option for the monitor that you want to shut off when you are playing the game, here is my MetaModes line

Option "MetaModes" "1280x1024,1280x1024;1280x1024,NULL; 1024x768,1024x768; 800x600, 800x600"

hope that helps

---

### Post by Knifa on 2006-10-14
> **CapnCook said:**
>  Open the /etc/X11/xorg.conf file and scroll down to the Device section listing your video card, on the options "MetaModes" line at the screen resolution you are running add NULL as the option for the monitor that you want to shut off when you are playing the game, here is my MetaModes line

Option "MetaModes" "1280x1024,1280x1024;1280x1024,NULL; 1024x768,1024x768; 800x600, 800x600"

hope that helps

Gave that a try, but it still ran in the middle, with both monitors on. Disabling the other monitor wouldn't be very good because I'd like to be able to see what's going on on the other one.

---

### Post by Knifa on 2006-10-14
Shameless bump. >_>

**Edit**: I've noticed that WoW shows the resolution as 2560x1024 rather than 1280x1024. D:

---

### Post by Knifa on 2006-10-19
No one?

---

### Post by kaiwondergoo on 2006-11-28
I'll bump this since I have the same problem. I did notice that WoW ran fine (in 1024x768 - borderless window) before it patched, only after did it distort and refuse to run at a decent res.

but, ya... same problem. nVidia 7950 gt /w 2 lcds.

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "G71"
    Option	   "NvAGP" "2"
    Option 	   "NoLogo" "1"
    Option 	   "RenderAccel" "1"
    Option 	   "CursorShadow" "1"
    Option 	   "Coolbits" "1"
    Option     	   "TwinView" "1"
    Option	   "MetaModes"	"1280x1024,1280x1024;1024x768,1024x768;800x600,800x600" 
EndSection
```

---

### Post by autocrosser on 2006-11-28
Well-the way I run UT2004 is with the 1280x1024-null in my xorg--after restarting X, I had the option for that size in my UT prefs--I don't know any way to have one screen play the game whilst surfing on the other--would be nice, but Xorg can not do this yet:neutral:  With the constant development of X, I would expect to see this at some point in time (I do not know when:-?)

The best way to do the xorg.conf is with the modeline as noted above--modify your file, then restart X or reboot to use it...

---

### Post by survient on 2006-12-30
well, if you guys are still interested, in your metamodes, instead of putting null, don't put anything, so it'll look like Option Metamodes "...1280x1024,1280x1024;[COLOR="Red"]1280x1024[/COLOR];1024x768,1024x768;".
By not adding the comma and a second res, it defaults it as null. Honestly I'd say try running the game in windowed mode if you want to still be able to see the stuff on the other monitor.

---

### Post by Palamedes on 2008-01-20
Howdy guys.  I know this is an old thread, but I thought I would toss out the solution I found.

Firstly make sure your windows are maximizing to a single monitor.  Open Firefox and maximize it.  If it maximizes to a single window then you likely have yoru xorg.conf file setup correctly.   If not, then you need to adjust your metamodes in the screen options of the xorg conf file.  I'm not going to go into that here as its pretty well covered on the forums.

Firstly log into the game in its current state and do your best to edit the video mode.  Set it to "Windowed Mode" but with Maximized unchecked.  

Exit the game.

Enter the WTF directory of your World of Warcraft install.

sudo vim Config.wtf

look for "SET gxResolution" and set it to your screen resolution.

That's it.  it should now work for you.  If you edit your Video settings again though it may reset your screen resolution in that file -- which I find annoying.

I know my screen resolution in the wtf file is set to 1680x1050... but it clearly says 3360x1050 in game, which is hard to play at.. 

Hope this helps

---

### Post by gmatt on 2008-05-02
that solution seems very specific to WoW, do you perhaps have a solution that works for Nexuiz? I have the exact same problem, but Nexuiz is a native linux game ... =(

---

