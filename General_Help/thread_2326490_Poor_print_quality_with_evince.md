---
title: "Poor print quality with evince"
date: 2016-06-01
forum: General Help
---

### Post by mike-g2 on 2016-06-01
I generally use evince to view pdfs, but when I print from the program the text and images are always less sharp

 ([IMG]http://ubuntuforums.org/attachment.php?attachmentid=269388&d=1464797464[/IMG]) 

than using lp directly

 ([IMG]http://ubuntuforums.org/attachment.php?attachmentid=269389&d=1464797478[/IMG]).  

My printer is a Brother HL-4570 and I'm running 14.04.  I have looked at my config file (~/.config/evince/print-settings) and compared it to my lp settings, but can't figure out what's wrong or how to fix this problem.  I have tried resetting my print-settings file to the system default, but to no avail.

Here's what lp is using
```
 
[~/.config/evince]$ lpoptions
BRColorMode=Normal BRImprovedGray=True BRPrintQuality=Auto BRReducedImage=False copies=1 device-uri=socket://ribosome.bio.utk.edu Duplex=DuplexNoTumble finishings=3 job-hold-until=no-hold job-priority=50 job-sheets=none,none marker-change-time=1464301415 marker-colors=#000000,#00FFFF,#FFFF00,#FF00FF,none,none,none marker-levels=-1,-1,-1,-1,-1,54,43 marker-names='Black\ Toner\ Cartridge,Cyan\ Toner\ Cartridge,Magenta\ Toner\ Cartridge,Yellow\ Toner\ Cartridge,Waste\ Toner\ Box,Belt\ Unit,Drum\ Unit' marker-types=toner,toner,toner,toner,waste-toner,other,opc number-up=1 PageRegion=Letter ppd-timestamp='Wed Jul  1 13:01:36 2015' printer-commands=AutoConfigure,Clean,PrintSelfTestPage printer-info='Brother HL-4570 CDW' printer-is-accepting-jobs=true printer-is-colormanaged=false printer-make-and-model='Brother HL-4570CDW BR-Script3' printer-state=3 printer-state-change-time=1464301415 printer-state-reasons=none printer-type=10522716 printer-uri-supported=ipp://localhost:631/printers/ribosome ScreenLock=True UCRGCRForImage=False

```

Here's my print-settings file
```

[Print Settings]
cups-BRColorMode=Normal
cups-UCRGCRForImage=False
print-at-time=
cups-Sleep=PrinterDefault
print-at=now
cups-Duplex=DuplexNoTumble
cover-before=none
cups-number-up=1
cups-BRPrintQuality=Auto
cups-ManualFeed=False
duplex=horizontal
cover-after=none
cups-InputSlot=AutoSelect
cups-BRJobHold=None
cups-TonerSaveMode=False
evince-print-setting-page-size=false
cups-BRImprovedGray=True
default-source=AutoSelect
evince-print-setting-page-scale=2
cups-BRMediaType=Plain
cups-ScreenLock=True
cups-BRReducedImage=False
cups-ImprovePrintOutput=None
cups-job-priority=50
cups-BRJobPIN=HoldKey0
evince-print-setting-page-autorotate=true
cups-job-sheets=none,none
cups-BRJobName=JobNameSystem
printer=ribosome
cups-CAPT=Fine

cups-BRSkipBlank=OFF
cups-BREnhanceBlkPrt=OFF
cups-BRMonoColor=Auto
cups-BRInputSlot=AutoSelect
cups-BRDuplex=DuplexTumble
cups-BRColorMatching=Normal
cups-BRReverse=OFF
cups-BRBlue=0
cups-BRContrast=0
cups-BRBrightness=0
cups-BRGreen=0
cups-BRSaturation=0
cups-BRImproveOutput=OFF
cups-BRResolution=600dpi
cups-BRGray=ON
cups-BRRed=0
cups-BRTonerSaveMode=OFF
cups-HPPhotoHalftone=Smooth
cups-HPGraphicsNeutralGrays=Black
cups-HPwmTextColor=Black
cups-HPBookletPageSize=Letter
cups-HPTextRGB=sRGB
cups-HPGraphicsRGB=sRGB
cups-HPServicesWeb=SupportAndTroubleshooting
cups-HPBookletScaling=Proportional
cups-HPEdgeControl=Normal
cups-HPManualDuplexOrientation=DuplexNoTumble
cups-HPGraphicsHalftone=Smooth

cups-HPBookletPageOrder=Normal
cups-HPPhotoRGB=sRGB
cups-HPwmPages=AllPages
cups-HPPhotoNeutralGrays=ProcessBlack
cups-CMAndResolution=CMYKImageRET2400
cups-HPTextHalftone=Smooth
cups-HPwmTextMessage=Draft
media-type=Unspecified
cups-HPwmSwitch=Off
cups-HPwmFontName=HelveticaB
cups-HPBookletFilter=False
cups-HPwmTextStyle=Medium
cups-HPManualDuplexSwitch=False
cups-HPwmBrightness=Medium
cups-HPBookletBackCover=False
cups-MediaType=Unspecified
cups-HPTextNeutralGrays=Black
cups-HPwmTextAngle=Deg45
cups-HPRotate180=False
cups-HPManualDuplexPrintGuide=False
cups-HPwmFontSize=pt48

cups-number-up-layout=lrtb
number-up-layout=lrtb

output-file-format=pdf

[Page Setup]
PPDName=Letter
DisplayName=US Letter
Width=215.89999389648438
Height=279.39999389648438
MarginTop=6.3499999999999996
MarginBottom=14.224
MarginLeft=6.3499999999999996
MarginRight=6.3499999999999996
Orientation=portrait


```

---

