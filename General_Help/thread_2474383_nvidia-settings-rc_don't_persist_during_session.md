---
title: "nvidia-settings-rc don't persist during session"
date: 2022-04-27
forum: General Help
---

### Post by issh on 2022-04-27
Hello, 

I am having a minor problem on my Ubuntu 22.04 Cinnamon desktop. The issue was present in the standard Ubuntu 22.04 installation I tried as well. My nvidia-settings-rc that I make through the Nvidia Settings program don't persist through the login session if the screen locks and I have to enter my password to unlock it, or if xScreensaver activates. To re-apply the nvidia-settings-rc after unlocking or clearing the screensaver I have to open the Nvidia Settings program to reapply my settings. The gamma and graphics quality are the only things I've adjusted. I followed instructions here: [https://manpages.ubuntu.com/manpages/jammy/man1/nvidia-settings.1.html](https://manpages.ubuntu.com/manpages/jammy/man1/nvidia-settings.1.html) and this worked as far as applying settings automatically when logging in. 

However to solve for the settings staying persistent during session I found this script here: [https://askubuntu.com/questions/421470/gnome-nvidia-overwriting-nvidia-settings-rc#:~:text=Open%20nvidia-settings%20and%20change%20brightness%20settings.%20Close%20it,are%20persisted%20between%20sessions%20try%20to%20reboot%20PC%3B](https://askubuntu.com/questions/421470/gnome-nvidia-overwriting-nvidia-settings-rc#:~:text=Open%20nvidia-settings%20and%20change%20brightness%20settings.%20Close%20it,are%20persisted%20between%20sessions%20try%20to%20reboot%20PC%3B) 

That question and answer is 8 years old though and applies to Ubuntu Unity. How would I apply that script for Ubuntu Cinnamon? Or is there a different solution? Scripts below: 

To be placed in usr/local/bin/ with +x flag to be used when switching users: 
nvidia_starter script
```
#!/bin/bash
debug=false
log_file="/var/log/nvidia_settings.log"
log () {
    if $debug ; then
    echo "`date "+%d/%m/%y %H:%M:%S"` :: $@" >> $log_file
    fi
}
dbus-monitor --sesion 
"type='signal',interface='com.canonical.Unity.Session',member='Unlocked'" | while  read line ; do 
    if [[ "$line" == *member=Unlocked* ]] 
    then
        log "$line"
        sh /usr/local/bin/nvidia_starter &
    fi
done

```

To be put into usr/local/bin/ with +x flag 
nvidia_starter script
```
#!/bin/bash
debug=false
log_file="/var/log/nvidia_settings.log"
log () {
if $debug ; then
    echo "`date "+%d/%m/%y %H:%M:%S"` :: $@" >> $log_file
fi
}
sleep 4
log "initializing nvidia settings."
nvidia-settings -l >> $log_file
log "nvidia settings initialized."
```
Then add to Startup Applications. 

Operating System: Ubuntu 22.04
Cinnamon Version: 5.2.7
Linux Kernel: 5.15.0-27-generic
Processor: Intel Core i5-2400
Memory: 15.6 GB
Graphic's Card: Nvidia Corporation GP106 [GeForce GTX 1060 6GB]
Nvidia Driver Version: 510.60.02
NVML Version: 11.510.60.02

Any suggestions?

---

### Post by TheFu on 2022-04-27
I've never seen any nvidia-settings or nvidia-xsettings program save configuration to the correct location.  I've always told it to save to my $HOME, then took that file and integrated it with the xorg.conf file in the normal /etc/ location.

So, what format is the resulting config file created by the tool?

OTOH, I don't have a 22.04 desktop anywhere. Don't have plans to put any physical systems on 22.04 w/ an nvidia GPU for at least 6 months, perhaps much longer.  I value stability, provided the system is still under support. *New* is the enemy of *stable*.

---

### Post by issh on 2022-05-03
> **TheFu said:**
> I've never seen any nvidia-settings or nvidia-xsettings program save configuration to the correct location.  I've always told it to save to my $HOME, then took that file and integrated it with the xorg.conf file in the normal /etc/ location. 

I would be grateful if you could explain this a little more? I've modified xorg.conf files before, just not sure about it here. 

> **TheFu said:**
> So, what format is the resulting config file created by the tool?

My .nvidia-settings-rc in the home directory looks like this: 

```
#
# /home/akiko/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA Settings utility
# Generated on Tue May  3 06:12:58 2022
#


# ConfigProperties:


RcFileLocale = C
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
UpdateRulesOnProfileNameChange = Yes
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = Memory_Used_(GPU_0),Yes,3000


# Attributes:


0/SyncToVBlank=1
0/LogAniso=4
0/FSAA=11
0/TextureClamping=1
0/FXAA=0
0/AllowFlipping=1
0/FSAAAppControlled=0
0/LogAnisoAppControlled=0
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=1
0/ShowGraphicsVisualIndicator=0
[DPY:DVI-D-0]/Dithering=0
[DPY:DVI-D-0]/DitheringMode=0
[DPY:DVI-D-0]/DitheringDepth=0
[DPY:DVI-D-0]/ColorSpace=0
[DPY:DVI-D-0]/ColorRange=0
[DPY:DVI-D-0]/SynchronousPaletteUpdates=0
[DPY:HDMI-0]/RedBrightness=0.000000
[DPY:HDMI-0]/GreenBrightness=0.000000
[DPY:HDMI-0]/BlueBrightness=0.000000
[DPY:HDMI-0]/RedContrast=0.000000
[DPY:HDMI-0]/GreenContrast=0.000000
[DPY:HDMI-0]/BlueContrast=0.000000
[DPY:HDMI-0]/RedGamma=0.775000
[DPY:HDMI-0]/GreenGamma=0.775000
[DPY:HDMI-0]/BlueGamma=0.775000
[DPY:HDMI-0]/Dithering=0
[DPY:HDMI-0]/DitheringMode=0
[DPY:HDMI-0]/DitheringDepth=0
[DPY:HDMI-0]/DigitalVibrance=0
[DPY:HDMI-0]/ColorSpace=0
[DPY:HDMI-0]/ColorRange=0
[DPY:HDMI-0]/SynchronousPaletteUpdates=0
[DPY:DP-0]/Dithering=0
[DPY:DP-0]/DitheringMode=0
[DPY:DP-0]/DitheringDepth=0
[DPY:DP-0]/ColorSpace=0
[DPY:DP-0]/ColorRange=0
[DPY:DP-0]/SynchronousPaletteUpdates=0
[DPY:DP-1]/Dithering=0
[DPY:DP-1]/DitheringMode=0
[DPY:DP-1]/DitheringDepth=0
[DPY:DP-1]/ColorSpace=0
[DPY:DP-1]/ColorRange=0
[DPY:DP-1]/SynchronousPaletteUpdates=0
[DPY:DP-2]/Dithering=0
[DPY:DP-2]/DitheringMode=0
[DPY:DP-2]/DitheringDepth=0
[DPY:DP-2]/ColorSpace=0
[DPY:DP-2]/ColorRange=0
[DPY:DP-2]/SynchronousPaletteUpdates=0
[DPY:DP-3]/Dithering=0
[DPY:DP-3]/DitheringMode=0
[DPY:DP-3]/DitheringDepth=0
[DPY:DP-3]/ColorSpace=0
[DPY:DP-3]/ColorRange=0
[DPY:DP-3]/SynchronousPaletteUpdates=0
[DPY:DP-4]/Dithering=0
[DPY:DP-4]/DitheringMode=0
[DPY:DP-4]/DitheringDepth=0
[DPY:DP-4]/ColorSpace=0
[DPY:DP-4]/ColorRange=0
[DPY:DP-4]/SynchronousPaletteUpdates=0
[DPY:DP-5]/Dithering=0
[DPY:DP-5]/DitheringMode=0
[DPY:DP-5]/DitheringDepth=0
[DPY:DP-5]/ColorSpace=0
[DPY:DP-5]/ColorRange=0
[DPY:DP-5]/SynchronousPaletteUpdates=0

```

As well my xinitrc file in /etc/X11/xinit/ looks like this: 

```
#!/bin/sh


# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)


# invoke global X session script
. /etc/X11/Xsession
nvidia-settings --load-config-only &
. /etc/X11/xinit/xinitrc

```

---

### Post by TheFu on 2022-05-04
~/.nvidia-settings-rc  needs an nvideo program to read it and run the settings.  I put that in ~/.xprofile as 
```
/usr/bin/nvidia-settings --load-config-only
```
I don't use any DE, so my setup is more like a desktop from 1995 than today.  ~/.xprofile is run by the login manager.  You'll need to discovery what your login manager and DE use for that.

/etc/X11/xinit/xinitrc isn't related.

You don't seem to have an xorg file, so all the defaults are being used.  That's normal.  I have one because there are to monitors and it is how I knew to control which was connected to the different outputs. Plus, I needed to manually force EDID monitor settings that weren't making it from the monitor, through my KVM switch through a DVI  -to- VGA adapter with the correct resolutions that the monitor prefers. 

In the olden days, every X/Windows server had to have an X11 config file to help the GPU and monitor communicate correctly.  Every computer had a very specialized xorg.conf file, since it was specific to the monitor(s) and the GPU(s).

I think for about the last decade, xorg server has done a good job of probing hardware to know which settings are supported, so 99% of people don't need any config file, unless they do something odd.  **The EDID standard did good** and generally works well, but not always.

---

### Post by issh on 2022-05-21
> **TheFu said:**
> ~/.nvidia-settings-rc  needs an nvideo program to read it and run the settings.  I put that in ~/.xprofile as 
```
/usr/bin/nvidia-settings --load-config-only
```
I don't use any DE, so my setup is more like a desktop from 1995 than today.  ~/.xprofile is run by the login manager.  You'll need to discovery what your login manager and DE use for that.

/etc/X11/xinit/xinitrc isn't related.

You don't seem to have an xorg file, so all the defaults are being used.  That's normal.  I have one because there are to monitors and it is how I knew to control which was connected to the different outputs. Plus, I needed to manually force EDID monitor settings that weren't making it from the monitor, through my KVM switch through a DVI  -to- VGA adapter with the correct resolutions that the monitor prefers. 

In the olden days, every X/Windows server had to have an X11 config file to help the GPU and monitor communicate correctly.  Every computer had a very specialized xorg.conf file, since it was specific to the monitor(s) and the GPU(s).

I think for about the last decade, xorg server has done a good job of probing hardware to know which settings are supported, so 99% of people don't need any config file, unless they do something odd.  **The EDID standard did good** and generally works well, but not always.

Hey, thank you for your explanation of X11 and the xorg.conf! I got it all sorted since you pointed me in the right direction. I learned a lot about this and now it's all working and my Nvidia settings now persist. I think for some distros and using an Nvidia GPU an xorg.conf file is needed to have settings apply and persist correctly. Though recently since I've asked this question Nvidia has started making their drivers open source and released kernel modules on GitHub. Don't know if you saw that. So hopefully in the future this mess with Nvidia GPUs and linux will be a thing of the past and it will then just work. Thanks for your response!

---

### Post by TheFu on 2022-05-21
Now we just need to get nVidia drivers to 
[LIST]
[*]stop phoning home 
[*]disabling much-wanted features in the F/LOSS drivers to encourage the use of proprietary drivers with tracking
[*]ending support of perfectly fine hardware years before it is dead.  I have a few nvidia GPUs that worked fine, but support was dropped and they effectively became bricks since the nouveau drivers won't support the native resolution of my main monitor.
[/LIST]

I've moved to AMD CPUs w/ integrated GPUs with my last build.  When the same GPU/iGPU gets cheap, I'll swap out the older Ryzen and nvidia GPU for it and effectively have 2 identical systems that work, no hassles.

If you aren't buying the very, very, high-end GPUs from nVidia, there's an AMD GPU/iGPU that will fit your needs with 100x less hassles.

---

### Post by issh on 2022-06-26
Yes you're right. It would be nice, but I doubt they will change their ways anytime soon. Also, they've been reducing GPU performance purposefully with driver and firmware updates on older GPUs. To get full performance we would typically have to buy enterprise grade GPUs. AMD is the way to go for sure, at least for using linux systems. Maybe Intel's new Arc GPUs will be great too. 
To your comment earlier, yes you're right. I recently learned the hard way that "new and shiny" isn't really the best for the most part. If something that is older is still supported why jump to something new right away? You're right.

---

