---
title: "&quot;Additional Drivers&quot; switching back to open-source drivers not working right."
date: 2019-04-06
forum: General Help
---

### Post by SagaciousKJB on 2019-04-06
I wasn't really sure where the best section for help with this would be.  Kind of a mix of multimedia, hardware and desktop environment problem.

Distribution: Xubuntu 18.04.2 TLS
XFCE: Ver 4.12
Motherboard:  ASRock AB350 Pro4
Card: Nvidia GeForce GTX 1070
Primary Display: Element 1080p Monitor connected via DVI->HMDI from PC to monitor
Secondary Display: AOC 720p Television connected via HDMI->HDMI from PC to television

Initial configuration (Default by installation):
Installed nouveau drivers as per the installation's default
Secondary Display was not present during installation.
Post-installation, upon plugging in the secondary display, XFCE/X.Org/whatever recognized it and configured it as a second screen in Xinerama mode

Initial configuration issues:
Video tearing on secondary TV display

Second configuration:
Installed nvidia's proprietary 390.116 drivers using "Additional Drivers" application.
Secondary Display was present during this installation.
Used Nvidia XSettings application to configure the displays the way I wanted (primary on the Element monitor, secondary on the AOC TV), enabled Xinerama, and reboot.

Second configuration issues:
Using disk encryption, the password prompt to unlock my partition and the login screen show up on the TV instead of my monitor upon boot
Conky doesn't seem to display correctly anymore
The first random freeze-up I've had on this PC

At this point, I decided the proprietary drivers weren't worth the trouble.  I don't plan to do much gaming on this, they didn't fix the video tearing, and they were easy enough to install, so I wanted to go back to the open-source ones to get better stability.

Upon reselecting the nouveau drivers, the XFCE "Display" settings in the "Settings Manager" didn't work correctly.  It would give me an error about having a different RandR version.  I Google'd and discovered this was caused by the xorg.conf file I'd created still being present, so I deleted that and rebooted.

After that the TV was still being selected as the primary screen, and the monitor wasn't getting a signal from a secondary display at all.  Not only that, but when I got into the "Display" settings in the "Settings Manager" section now, it only showed one display available to configure.  There is a check box to "Configure new displays when connected" and I checked that, hoping I could just unplug the TV and plug it back in once the PC had booted and displayed the primary screen on the Element monitor.  I disconnected the TV, and it would load and display on the Element monitor like it should, but then when I plug the HDMI cable into the back of the AOC TV it no longer automatically configures a new display.

---

### Post by pqwoerituytrueiwoq on 2019-04-06
Screen tearing with nvidia drivers can be handled by the 'force full composition pipeline' feature under display configuration, this is hidden behind the advanced button at the bottom
this needs to be applied to both displays, i had had issues with applying this at via Xorg configs that result in a black screen, at this time i have a keyboard shortcut to apply my configs

```

#!/bin/sh
# this script is named /usr/local/bin/config_displays
if [ -z "$1" ];then # dual monitor / productivity
    nvidia-settings --assign CurrentMetaMode="DP-0: nvidia-auto-select +1920+0 {ForceFullCompositionPipeline=On}, HDMI-0: nvidia-auto-select +0+0 {ForceFullCompositionPipeline=On}"
    xrandr -d :0 --output HDMI-0 --auto --output DP-0 --primary --refresh 60 --mode 1920x1080 --right-of HDMI-0
    xfconf-query -c xfwm4 -p /general/use_compositing -t bool -s true
    # make sure panels are set right
    xfconf-query -c xfce4-panel -p /panels/panel-3/autohide-behavior -t int -s 0
    xfconf-query -c xfce4-panel -p /panels/panel-4/autohide-behavior -t int -s 0
    # this panel plugin likes to copy the other video out, so it needs to the toggle to ensure it works properly
    xfconf-query -c xfce4-panel -p /plugins/plugin-11/include-all-monitors -t bool -s true
    xfconf-query -c xfce4-panel -p /plugins/plugin-11/include-all-monitors -t bool -s false
elif [ "$1" = "toggle" ];then
    ssh pi@10.0.0.25 irsend SEND_ONCE tv KEY_POWER # use Raspberry pi to turn tv on /off
    if [ "$(xfconf-query -c xfwm4 -p /general/use_compositing)" = "false" ];then # normal use
        notify-send --icon info "Waiting for TV" -t 9000
        sleep 9 # tv response time
        config_displays
    else # gaming mode
        xfconf-query -c xfwm4 -p /general/use_compositing -t bool -s false
        if [ -z "$2" ];then # freesync, desktop compositioning only outputs 60fps rendering a 120/144hrz display pointless over a 60hrz one, unless you only care about the mouse cursor as well as breaking freesync
            nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 {ForceCompositionPipeline=Off, AllowGSYNCCompatible=On}"
            xrandr -d :0 --output HDMI-0 --off --output DP-0 --primary --refresh 144 --mode 1920x1080
        else # some games are locked at 60 fps, so this is for them, but why not just use normal mode at this point?
            nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 {ForceCompositionPipeline=On, AllowGSYNCCompatible=Off}"
            xrandr -d :0 --output HDMI-0 --off --output DP-0 --primary --refresh 60 --mode 1920x1080
            emulationstation & #mode is pointless for anything else
        fi
        # hide overlapping panels
        xfconf-query -c xfce4-panel -p /panels/panel-3/autohide-behavior -t int -s 2
        xfconf-query -c xfce4-panel -p /panels/panel-4/autohide-behavior -t int -s 2
    fi
fi
exit 0

```
You may want to use/try a newer driver from this ppa: 
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

I think the login dialog appears on what ever display the mouse cursor is on, i have noticed playing around with some uefi video settings in my bios makes it decide what display to use as primary for booting

---

### Post by SagaciousKJB on 2019-04-07
> **pqwoerituytrueiwoq said:**
> Screen tearing with nvidia drivers can be handled by the 'force full composition pipeline' feature under display configuration, this is hidden behind the advanced button at the bottom
this needs to be applied to both displays, i had had issues with applying this at via Xorg configs that result in a black screen, at this time i have a keyboard shortcut to apply my configs

```

#!/bin/sh
# this script is named /usr/local/bin/config_displays
if [ -z "$1" ];then # dual monitor / productivity
    nvidia-settings --assign CurrentMetaMode="DP-0: nvidia-auto-select +1920+0 {ForceFullCompositionPipeline=On}, HDMI-0: nvidia-auto-select +0+0 {ForceFullCompositionPipeline=On}"
    xrandr -d :0 --output HDMI-0 --auto --output DP-0 --primary --refresh 60 --mode 1920x1080 --right-of HDMI-0
    xfconf-query -c xfwm4 -p /general/use_compositing -t bool -s true
    # make sure panels are set right
    xfconf-query -c xfce4-panel -p /panels/panel-3/autohide-behavior -t int -s 0
    xfconf-query -c xfce4-panel -p /panels/panel-4/autohide-behavior -t int -s 0
    # this panel plugin likes to copy the other video out, so it needs to the toggle to ensure it works properly
    xfconf-query -c xfce4-panel -p /plugins/plugin-11/include-all-monitors -t bool -s true
    xfconf-query -c xfce4-panel -p /plugins/plugin-11/include-all-monitors -t bool -s false
elif [ "$1" = "toggle" ];then
    ssh pi@10.0.0.25 irsend SEND_ONCE tv KEY_POWER # use Raspberry pi to turn tv on /off
    if [ "$(xfconf-query -c xfwm4 -p /general/use_compositing)" = "false" ];then # normal use
        notify-send --icon info "Waiting for TV" -t 9000
        sleep 9 # tv response time
        config_displays
    else # gaming mode
        xfconf-query -c xfwm4 -p /general/use_compositing -t bool -s false
        if [ -z "$2" ];then # freesync, desktop compositioning only outputs 60fps rendering a 120/144hrz display pointless over a 60hrz one, unless you only care about the mouse cursor as well as breaking freesync
            nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 {ForceCompositionPipeline=Off, AllowGSYNCCompatible=On}"
            xrandr -d :0 --output HDMI-0 --off --output DP-0 --primary --refresh 144 --mode 1920x1080
        else # some games are locked at 60 fps, so this is for them, but why not just use normal mode at this point?
            nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 {ForceCompositionPipeline=On, AllowGSYNCCompatible=Off}"
            xrandr -d :0 --output HDMI-0 --off --output DP-0 --primary --refresh 60 --mode 1920x1080
            emulationstation & #mode is pointless for anything else
        fi
        # hide overlapping panels
        xfconf-query -c xfce4-panel -p /panels/panel-3/autohide-behavior -t int -s 2
        xfconf-query -c xfce4-panel -p /panels/panel-4/autohide-behavior -t int -s 2
    fi
fi
exit 0

```
You may want to use/try a newer driver from this ppa: 
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

I think the login dialog appears on what ever display the mouse cursor is on, i have noticed playing around with some uefi video settings in my bios makes it decide what display to use as primary for booting

Thanks for the tip on the FullCompositionPipeLine option, that took care of the video tearing.

Still having trouble with it booting the login-prompt on the TV instead of the monitor, but I guess I'll try to fiddle around in the BIOS.  Or is it called UEFI now?  I am very out of date with this stuff.

---

