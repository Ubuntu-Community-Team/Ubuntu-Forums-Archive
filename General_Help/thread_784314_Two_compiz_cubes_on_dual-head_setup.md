---
title: "Two compiz cubes on dual-head setup?"
date: 2008-05-06
forum: General Help
---

### Post by 01000111 on 2008-05-06
Greetings all,
I'm running Xubuntu v8.04 and have a nVidia GeForce FX 5200 with 2 VGA ports. One port has a widescreen LCD monitor running at 1680x1050, and the other port has a generic CRT running at 1280x1024. When I installed Compiz fusion, everything worked well (cube, switchers, etc), but everything was centered around the logical middle of the entire screen area, which meant that parts of every switcher, cube, and window effect were split across the two monitors... rather distracting.

Is it possible to have compiz use the two monitors separately? My (compiz noob) thinking is to have two cubes, one on each monitor with different hotkeys for each.

Is this possible? Is there a better solution?

Any assistance is appreciated. Thx.

Also, if anyone has a good HowTo for compiz install on Xubuntu 8.04, that would be helpful too...  i'm sure I went the long way around.

01000111

---

### Post by Achtung on 2008-05-06
Install the compizconfig-settings-manager if you don't already have it.

In the "Desktop cube" plugin dialog, click the "general" tab. Change the "multi output mode" option to have multiple cubes. 

IIRC, both cubes are activated at the same time with one key & mouse combo. The current workspaces displayed on screen #1 and screen #2 should be consecutive workspaces, as in "workspace #1 on left screen and workspace #2 on right screen". When you rotate, I recall that both should turn at the same time, while keeping the consecutive order, as in "when I turn my 4 workspaces cube 90 degrees, I go from workspace #1 to workspace #2 on the left screen, and from workspace #2 to workspace #3 on my right screen". 

Things might have changed, but that's pretty much how I was setup when I had dual screens (changed for a laptop now). Anyone is free to correct me, here ;)

---

### Post by 01000111 on 2008-05-06
> **Achtung said:**
> Install the compizconfig-settings-manager if you don't already have it.

In the "Desktop cube" plugin dialog, click the "general" tab. Change the "multi output mode" option to have multiple cubes. 

<snip>


Thanks, but that doesn't seem to do it.  I have set the following:
 General Options, Display Settings, 
    Detect Outputs: <unchecked>
    Outputs: 1680x1050+0+0,1280x1024+0+0
 Shift Switcher, Appearance
    Multi Output Mode: On activated output

But everything still works with a single virtual desktop and not with two separate screens.

Other ideas?

<EDIT>
I'm told in other forums that I should be using Twinview mode, but my screens are working perfectly now, and when I add the Twinview options, it mangles the resolution.  Attached is my xorg.conf.  Any assistance is appreciated.
</EDIT>

01000111

---

### Post by 01000111 on 2008-05-07
Solved!!!  All I had to do was disable Xinerama, then I got my two cubes.  Thanks all.

01000111

---

### Post by spotdart on 2008-11-08
when I hit the key combo it activates both cubes, and I am pretty sure that's the intended behavior. ideally the cube would only activate on the desktop that the cursor was on. is there any way to accomplish this?

---

### Post by VortexCortex on 2009-01-18
If you want the desktops to be independent of each other then enable "separate X Screen"

Plug in and turn on all screens you plan on using.

Open the NVIDIA X Server Settings via terminal eg:

```
sudo nvidia-settings
```

Select X Server Display Configuration from the list on the left.

Click the "Detect Displays" button.

Select "Separate x screen" from the "Configuration:" option.

Be sure to select a primary display by choosing "Absolute" from the "Position" option of the "X Screen" tab.

Select each display from the layout area and select their positions as well.

Make sure "Enable Xinerama" is disabled if you plan to use Compiz.

Click the "Save to X Configuration File" button.

Enable the "Merge with Existing File" option if it is not already enabled.

Click the "Save" button.

Note: If you launch the "NVIDIA X Server Settings" from the system menu and you are do not have root privlages you will not be able to save the settings.  This is why we used "sudo" from the terminal instead.

Click "Quit" to exit the nvida-settings manager.

Reboot your system:

```
sudo shutdown now -r
```

Now each display will have its own X-Screen.

This means that each screen has its own desktop cube as well.
Note: you can not move windows between the displays, and some programs will only run on one display at a time (Firefox, and Transmission for example)

I prefer to use Twinview instead of this configuration, but my current displays support different resolutions.

---

