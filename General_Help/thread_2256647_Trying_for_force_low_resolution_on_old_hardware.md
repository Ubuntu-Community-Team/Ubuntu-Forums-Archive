---
title: "Trying for force low resolution on old hardware"
date: 2014-12-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-12-13
So i have this old box with a crappy video chipset, plenty of vram, just a crappy chipset
i want to force 800x600 at 60hrz
it was defaulting to 1920x1080_60 i managed to force 800x600 but it is running at 75Hrz
i am trying to get the frame rate bearable, say 20-25fps
here is what i did with Xorg
```
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Modes     "800x600"
                Depth     24
        EndSubSection
EndSection
```
i want to keep this generic, as far as i know every display supports 800x600 for fallback reasons
i am dealing with this onboard chip
```
~$ lspci|grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

---

### Post by shantiq on 2014-12-14
maybe try [this]("http://ubuntuforums.org/showthread.php?p=8595940")

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

**xrandr**
and then tweek settings to suit you here

```
[B]xrandr --help
[/B]
usage: xrandr [options]
  where options are:
  --display <display> or -d <display>
  --help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --current
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --scale-from <w>x<h>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [flags...]
            Valid flags: +HSync -HSync +VSync -VSync
                         +CSync -CSync CSync Interlace DoubleScan
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
  --listproviders
  --setprovideroutputsource <prov-xid> <source-xid>
  --setprovideroffloadsink <prov-xid> <sink-xid>



```


more info[ here]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")   and generally [here]("https://www.google.co.uk/search?q=change+screen+resolution+command+line+ubuntu&hl=en-GB&gbv=2&oq=change+screen+resolution+command&gs_l=heirloom-serp.1.4.0l4j0i20j0i22i30l5.132180.146027.0.150632.36.31.2.3.3.0.176.2136.30j1.31.0.msedr...0...1ac.1.34.heirloom-serp..0.36.2181.fIHDUTAp2Xg")


just had an issue about resolution yesterday; so i am no specialist this is just "things i found" and thought might feasibly help you here

---

