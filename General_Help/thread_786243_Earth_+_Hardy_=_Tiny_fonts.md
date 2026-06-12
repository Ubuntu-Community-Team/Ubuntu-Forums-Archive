---
title: "Earth + Hardy = Tiny fonts"
date: 2008-05-07
forum: General Help
---

### Post by IHATEDLINK on 2008-05-07
Heeeey
I just installed Google Earth on Ubuntu Hardy Heron and it works great, but the fonts are really tiny, i mean, take a look at this snapshots:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69202&stc=1&d=1210218737[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69203&stc=1&d=1210218737[/IMG]

Any help would be very appreciated.

---

### Post by stinger30au on 2008-05-08
i had same problem. i fixxed it myself. i went in to add/remove programs and installed microsoft fonts. restart pc. fixxed

---

### Post by IHATEDLINK on 2008-05-08
Thanks a lot mate. I'km gonna try that right now.

---

### Post by adonet on 2008-05-09
Did it work out for you?

I think in the repos its called msttcorefonts

---

### Post by esteckis on 2008-05-09
This is to change the font size if they are too small.
gedit ~/.config/Google/GoogleEarthPlus.conf   

 What you want to change is:    **GUIFontSize=12**

Please disregard, I guess the newer version of GE does not let you change the font this way.  I just tried it and no go. I happen to see it on another post.

---

### Post by Stacks on 2008-07-12
Hey, don't disregard it worked fine for me.

Dell GX280 with NVIDIA 7900 GTX running UBUNTU 8.04 (hardy)
I set GUIFontSize=18                                        :lolflag:

---

### Post by secular on 2008-08-03
> **esteckis said:**
> This is to change the font size if they are too small.
gedit ~/.config/Google/GoogleEarthPlus.conf   

 What you want to change is:    **GUIFontSize=12**

[deletia]


Apologies for jumping in here....

I opened that file and noticed two places that listed font size. I changed the first, and nothing happened. I then changed the second--and that worked. 

The fonts in GE are larger and readable for me now.

Also, before I did this, I shut down GE and deleted a a temporary GoogleEarthPlus.conf file that I saw next to GoogleEarthPlus.conf.

Thanks for the tip!

---

### Post by rEbyTer on 2008-08-03
It works. thank you.

---

### Post by grouchyolddude on 2008-08-16
WoW... sorry about the multiple posts in regards to this, but every time I search, with a slightly different word content, I get back a more relevant thread, or another fix.

I installed the ms fonts from the repository, but it hasn't solved the font issue on GE for me. 
  I also tried to change the font size in GE, by entering >  gedit ~/.config/Google/GoogleEarthPlus.conf


but I fail to see any setting for fonts to change.

> [General]
AnimSpeed=1
CachePath=/root/.googleearth/Cache
ClampBegin=false
ControllerEnabled=false
ControllerMode=2
DisableNavCheckbox=false
InvertMouseWheel=false
KMLPath=/root/.googleearth
Key="KF2vnIDUh1c="
LogoutClean=true
NavMode=0
NavigatorShow=0
PolyEditXPos=69
PolyEditXSize=422
PolyEditYPos=74
PolyEditYSize=552
RepeatMode=1
ReverseControls=false
SMode=true
SwoopEnabled=true
TimeFolderRestrict=false
TimeShow=1
TimeZoneHours=-6
TimeZoneMinutes=0
TimeZoneMode=1
TimeZoneName=Local
UID="0TsuRF0Wp27Uw6ss7bWoaQ=="
VID="AAAADTQuMy43MjA0LjA4MzY="
currentVersion=4.3.7204.0836
defaultBrowser=true
enableTips=true
hiddenWindows-4_3=@Invalid()
lastHeight=693
lastLeft=0
lastTip=9
lastTop=0
lastWidth=1024
layersOpen=true
mouseWheelSpeed=1
osName=Linux
placesOpen=true
renderWarning-OGLsoftwareEmulated=false
searchOpen=true
shown_GPS=false
shown_LeftPanel=true
shown_RenderFrame=true
shown_Ruler=false
visibleWindows-4_3=RenderWindow, ServerWindow
wasFullScreen=false
wasMaximized=true

[Layer]
FlySpeed=0.171
drivingDirectionsRange=1000
drivingDirectionsSpeed=150
drivingDirectionsTilt=45
pauseTime=1.6
tourBalloonShow=false
tourCycles=1
tourSpeed=0.171

[Render]
CompassVisible=true

[UsageStatistics]
firstRun\day=13
firstRun\hour=21
firstRun\minute=1
firstRun\month=8
firstRun\second=55
firstRun\year=2008
loginHistory=0
numRuns=10
numRunsThisVersion=10
prevRun\day=16
prevRun\hour=9
prevRun\minute=47
prevRun\month=8
prevRun\second=24
prevRun\year=2008

[autoupdate]
InstalledVersion=4.3.7204.836

---

### Post by grouchyolddude on 2008-08-16
SOLVED.. by adding > GuiFontFamily=Arial
GuiFontSize=18
to the gogle config. file, in the [render] area, just below the line "CompassVisible=true"

> [Render]
CompassVisible=true
GuiFontFamily=Arial
GuiFontSize=18

---

### Post by Francois_C on 2008-12-27
Thank you very much, grouchyolddude.

I experienced this issue since I replaced my 1280x1024 display with a 1680x1050 one.

I get the best results (almost same display as before) with:

[Render]
CompassVisible=true
FeetMiles=false
GuiFontFamily=Sans Serif
GuiFontSize=8

I think GoogleEarth programmers should fix that issue, which is rather boring.

---

### Post by mindhaq on 2009-03-01
For me, this is still not working, all text is small and unreadable. Even very large font sizes in the .conf file (like 28) change nothing. I'm sure it is the right file, because it gets touched when starting GE.

I do have msttcorefonts installed, and tried it with GUIFontFamily Arial and Sans Serif.

No difference.

So - any other ideas?

---

### Post by Francewhoa on 2010-03-21
Same here. Default fonts are too small in Google Earth 5. **The following worked for me.** [http://ubuntuforums.org/showthread.php?p=9004685#post9004685](http://ubuntuforums.org/showthread.php?p=9004685#post9004685)

---

