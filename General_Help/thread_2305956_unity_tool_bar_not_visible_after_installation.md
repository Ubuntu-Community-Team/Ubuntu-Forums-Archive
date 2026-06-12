---
title: "unity tool bar not visible after installation"
date: 2015-12-10
forum: General Help
---

### Post by Old Jimma on 2015-12-10
Hi Community:

I'm installing 14.04 and have a 42" HD monitor.

When I install 14.04, I can't see the tool bar that is supposed to be on the right or the bar with the shut down button on the top.

However, when I install 14.04 with a 24" monitor it is there.

What do I have to do to see the side and top tool bars. I fiddled arround with displays and nothing worked.

Thanks,
Old Jimma
Here since Hoary Hedge Hog

---

### Post by grahammechanical on 2015-12-10
You can try right clicking the desktop wallpaper and if a menu appears select Change Desktop Background. That will open System Settings at the Appearance tab but from there you can get to the System Settings main window. Then select Software & Updates>Additional Drivers tab. And then change video drivers. Perhaps using the open source video to see if that gets you to a working desktop. You need to be connected to the internet and to allow time for Additional Drivers to do its stuff but you should get an offer of several video drivers.

Is the only difference that between the 42 inch and the 24 inch monitors? Or are the monitors attached to different hardware?

Another option is the select Advanced options for Ubuntu from the Grub boot menu and then select recovery mode and at the recovery menu select Resume. That might also get you to a working desktop from which you can change video drivers.

Regards

---

### Post by sandyd on 2015-12-10
> **Old Jimma said:**
> Hi Community:

I'm installing 14.04 and have a 42" HD monitor.

When I install 14.04, I can't see the tool bar that is supposed to be on the right or the bar with the shut down button on the top.

However, when I install 14.04 with a 24" monitor it is there.

What do I have to do to see the side and top tool bars. I fiddled arround with displays and nothing worked.

Thanks,
Old Jimma
Here since Hoary Hedge Hog
If it is HDMI, you may need to adjust the overscan on the monitor.
If its a old monitor that doesn't have the options for overscan, or you just don't want to change it on the monitor side, try the below:

Note that this is for the display "HDMI-1", yours may be different. Check xrandr for the correct value.
Also, replace the resolution (in italics) with your own, which is also viewable in xrandr.
```

xrandr --output HDMI-1 --set underscan on  ## Overscan On
xrandr --output HDMI-1 --fb *1024x768* --transform 1,0,[COLOR="#FF0000"]-30[/COLOR],0,1,[COLOR="#0000FF"]-10[/COLOR],0,0,1 ## Set overscan

```
The red value controls the sides, the blue value controls the top/bottom

To reset the changes, do
```

xrandr --output HDMI-1 --fb *1024x768* --transform none
```

You can also adjust this with the proprietary drivers if your card is ati or nvidia, and is supported with the current driver version.

---

