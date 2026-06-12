---
title: "googleearth 3.4 installation and small fonts - help needed"
date: 2008-04-17
forum: General Help
---

### Post by | MM | on 2008-04-17
Hi,

I have just installed the latest version of googleaearth.  I let it install in /opt/googleearth because id rather it there than my /home folder.  The previous version seemed to work fine following this method.

The latest version however, seems to only login to the google earth server when i launch it with sudo!  Without sudo, Google earth opens but wont login and no earth is displayed.  I tried modifying the permissions of /opt/googleearth/ so that all users can read and write files but that hasn't changed anything.

Also, the fonts are really small, and I've tried :
```

echo 12 > ~/.googleearth/Registry/google/googleearthplus/User/render/guifontsize

```

...which doesn't seem to work either.


Any thoughts from those of you savvy in the ways of Ubuntu and googleearth?


Otherwise when i do run it, it is a very nice version, much much smoother on my system  and they've made it more beautiful as well!  Barring my issues, highly recommended!

---

### Post by | MM | on 2008-04-18
bump

---

### Post by staskam on 2008-04-19
gedit ~/.config/Google/GoogleEarthPlus.conf

---

### Post by | MM | on 2008-04-20
> **staskam said:**
> gedit ~/.config/Google/GoogleEarthPlus.conf


Dude you are a legend!!  Thanks, i fixed the font size.  Also the file was set up with only root permissions so allowing others to read and write fixed the other issue of google-earth not logging in and rendering the world etc etc ...

Many thanks!

---

### Post by tubbygweilo on 2008-04-27
> **staskam said:**
> gedit ~/.config/Google/GoogleEarthPlus.conf
Many thanks.

---

### Post by godown on 2008-05-07
hi all,
i'm a new member of the forum, i have the same problem but i dont know how to fix it...

this is my conf file, which setting should i change?

[General]
AnimSpeed=1
CachePath=/home/godown/.googleearth/Cache
ClampBegin=false
ControllerEnabled=false
ControllerMode=2
InvertMouseWheel=false
KMLPath=/home/godown/.googleearth
Key="O4JblQ1sRiA="
LogoutClean=true
NavigatorShow=0
PolyEditXPos=51
PolyEditYPos=68
RepeatMode=1
ReverseControls=false
SMode=true
SwoopEnabled=true
TimeFolderRestrict=false
TimeShow=1
TimeZoneHours=2
TimeZoneMinutes=0
TimeZoneMode=1
TimeZoneName=Local
UID="NUIhfooKLMj+TzEgsH8Dzg=="
VID="AAAADTQuMy43MjA0LjA4MzY="
currentVersion=4.3.7204.0836
defaultBrowser=true
enableTips=true
hiddenWindows-4_3=@Invalid()
lastHeight=694
lastLeft=1
lastTip=4
lastTop=48
lastWidth=1359
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
firstRun\day=7
firstRun\hour=19
firstRun\minute=31
firstRun\month=5
firstRun\second=42
firstRun\year=2008
loginHistory=0
numRuns=3
numRunsThisVersion=3
prevRun\day=7
prevRun\hour=19
prevRun\minute=38
prevRun\month=5
prevRun\second=36
prevRun\year=2008

[autoupdate]
InstalledVersion=4.3.7204.836

thanx

---

### Post by Yumi on 2008-05-09
My Render section looks different to yours: The bold value GuiFontSize=12 is what I changed. Set it to the value you like.

[Render]
AnisotropicFiltering=0
CompassVisible=true
DisableAdvancedFeatures=false
ElevationExaggeration=1
FeetMiles=false
GridReference=0
GuiFontFamily=Arial
**GuiFontSize=12**
GuiFontStyle=0
GuiFontWeight=50
IconSize=2
OverviewSize=34
OverviewZoom=99
PrimaryFontVersion2Family=Arial
PrimaryFontVersion2Size=18
PrimaryFontVersion2Style=0
PrimaryFontVersion2Weight=75
RenderingApi=1
SecondaryFontVersion2Family=Bitstream Vera Sans
SecondaryFontVersion2Size=18
SecondaryFontVersion2Style=0
SecondaryFontVersion2Weight=75
TerrainQuality=-1
TextureColors=1
TextureCompressionDXTC=true


Also my installed version is different. Maybe you should upgrade (or me????)

[autoupdate]
InstalledVersion=4.3.7191.6508

---

### Post by godown on 2008-05-09
> 
Also my installed version is different. Maybe you should upgrade (or me????)


Yes the conf file is not exactly the same! :) that's why I can't find the GUI parameter... My version is 4.3.7204.836, the latest downloadable from google sites...

> 
The bold value GuiFontSize=12 is what I changed. Set it to the value you like.


I cut and paste your render section into mine... except for the font size that I've set to 18...maybe because I dont have microsoft fonts installed...but I dont really mind... Now worked...

Thanks for post your conf file and for the reply.

bye :lolflag:

[Render]
AnisotropicFiltering=0
CompassVisible=true
DisableAdvancedFeatures=false
ElevationExaggeration=1
FeetMiles=false
GridReference=0
GuiFontFamily=Arial
GuiFontSize=18
GuiFontStyle=0
GuiFontWeight=50
IconSize=2
OverviewSize=34
OverviewZoom=99
PrimaryFontVersion2Family=Arial
PrimaryFontVersion2Size=18
PrimaryFontVersion2Style=0
PrimaryFontVersion2Weight=75
RenderingApi=1
SecondaryFontVersion2Family=Bitstream Vera Sans
SecondaryFontVersion2Size=18
SecondaryFontVersion2Style=0
SecondaryFontVersion2Weight=75
TerrainQuality=-1
TextureColors=1
TextureCompressionDXTC=true

---

### Post by Yumi on 2008-05-10
Glad it is working now.

Just one point. I use google-earth from ubuntu synaptics. Had to include an extra repository. Has the added advantage that it notifies you when future updates become available.

Michael

---

