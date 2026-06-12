---
title: "black screen every time TV turns back on with htpc with intel HD2000"
date: 2016-03-13
forum: General Help
---

### Post by sns2 on 2016-03-13
My htpc screen stays black and fails to come back on each time I turn off my TV and then turn it back on.

I am forced to shell in and sudo reboot each time

Intel HD2000 built in graphics.  

EDIT:  Ubuntu 14.04 LTS

i tried making a keyboard shortcut for
xrandr --auto
and 
kill xsettingsd

but these shortcuts seemingly do nothing.

I found the link below, I installed xtrace, but dont know how to proceed, or even if its relevant:

"[COLOR=#333333][FONT=Ubuntu Beta]To debug this problem, check if [/FONT][/COLOR]gnome-settings-daemons[COLOR=#333333][FONT=Ubuntu Beta] is getting a signal that the display configuration has changed, by running [/FONT][/COLOR]**xtrace**[COLOR=#333333][FONT=Ubuntu Beta] against it, and look for a [/FONT][/COLOR]RRScreenChangeNotify[COLOR=#333333][FONT=Ubuntu Beta] event when resuming the machine. If that signal is being sent, then it indicates a possible bug in g-s-d. Otherwise, it suggests a bug in either X or (more likely) the kernel which is not causing the signal to be emitted to begin with."  [/FONT][/COLOR]https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen#Problem:__Black_screen_after_resume

---

### Post by grahammechanical on 2016-03-13
I do not like to make assumptions. It wastes time by going in the wrong direction.

What computer operating system are you using? And what settings does it have for turning off the screen when inactive?

Regards.

---

### Post by sns2 on 2016-03-13
Sorry, i forgot :-)  it is Ubuntu 14.04 LTS.

Under System Settings > Brightness and Lock > Lock is disable is off.  And Dim screen to save power is off.

Under Security and Privacy, everything is disabled, set not to lock.

Under Power settings, it is set to not suspend.

thank you

---

### Post by montag dp on 2016-03-13
You might want to have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=2316298](http://ubuntuforums.org/showthread.php?t=2316298)

I'd recommend the following.  First, determine the name of your TV and laptop displays using this command:

```
xrandr -q
```

Then, before turning off or disconnecting the TV, run this:

```
xrandr --output <name of TV display> --off
xrandr --output <name of laptop display> --auto
```

where <name of ... display> is replaced by the names you found out from xrandr -q.  The second command in the code block above may or may not be needed.  If that solves the problem, consider putting it in a script with a launcher or hotkey and run it whenever you are going to disconnect or turn off the TV. There are also xrandr commands that can be run when the TV is plugged in / turned on to make sure it goes in the right spot, if needed.  See, for example, the --right-of and --left-of options in the xrandr man pages.  I can help with that later if you need it.

---

### Post by sns2 on 2016-03-13
thanks. This is not a laptop, just a desktop HTPC.


i did xrandr -q

```

Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 2037mm x 1146mm
   1920x1080      60.0*+   59.9     30.0     24.0     30.0     24.0
   1920x1080i     60.1     60.0
   1280x1024      60.0
   1360x768       59.8
   1280x720       60.0     59.9
   1024x768       60.0
   800x600        60.3
   720x480        60.0     59.9
   720x480i       60.1     60.1
   640x480        60.0     59.9
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

Then I did:

xrandr --output HDMI1 --off


And the screen turned off.  

Then I turned off the TV.  When I turned the TV back on, it still did not work, but a little differently. Instead of getting the typical black screen, I get a "blue screen" which means my TV thinks it has no signal and within a few minutes the TV will shut itself off.

---

### Post by montag dp on 2016-03-13
Okay, so are you saying that you are using the TV as your primary display?  It's not a dual-monitor setup?

---

### Post by sns2 on 2016-03-13
> **montag dp said:**
> Okay, so are you saying that you are using the TV as your primary display?  It's not a dual-monitor setup?

that's right, single display which is my TV.

---

### Post by montag dp on 2016-03-13
I see. That makes it more difficult, because in my experience, I've never been able to get an HDMI display to be automatically detected. In any case, when you get the blue screen, you should be able to enable the display if you can issue the command:

```
xrandr --output HDMI1 --auto
```

Of course, you will probably have to do this "blind" by opening the terminal with its keyboard shortcut (probably Ctrl+Alt+T, but I'm not sure because I don't run Unity) and then typing it. Or you can put it in a script with its own keyboard shortcut. You may also have to log in blind if your session is locked, so I know this isn't an ideal solution. I don't know how to get HDMI outputs to be detected automatically, though, so maybe this is an acceptable workaround if you definitely want to have the TV as your main display. 

If someone knows how to make HDMI displays be detected automatically, I'd definitely like to know too, though.

---

### Post by sns2 on 2016-03-13
Thanks, so  i bound a kybd shortcut for the command

xrandr --output HDMI1 --auto
i ran this once before turning the TV off, then turned off the TV, expecting it not to come back on as usual.

For whatever reason the TV came on this time without me having to run the command.

Usually, after the TV is off all night, it will never come on in the morning.  

I don't know if it is because I am turning it back on so soon and not waiting overnight that it is now working.

Is it possible that running that command just once somehow fixed the problem?

I guess we'll see tomorow.

---

### Post by montag dp on 2016-03-13
I don't know.  I would have suggested xrandr --output HDMI1 --off to turn it off, and then xrandr --output HDMI1 --auto to turn it back on, but whatever works!  Sometimes the displays work in mysterious ways...

---

### Post by mastablasta on 2016-03-14
have you tried something like mythbuntu or openelec if this is a media center?

if this is a Workstation then you should see how tv is recognised. it lok like the TV sends "off" signal to output and then it stays on off.

for example RaspberryPi i use for media center would dim the screen after some time. when i turn it on it would sometimes not react and wake up. turns out it have to give the TV (an LG LCD) a signal (with remote) that a HDD device is pluged in. once i do that remote activates the Pi and wakes it up from dimmed state. so perhaps in your case the TV needs to give it a kick.

---

### Post by shivani_sharma on 2016-03-14
Fresh install of Xubuntu, update to date, latest upgrade, now lost audio support. Have followed all correction procedures found online, but still no sound. Sound works on Winders. Must I ...

---

### Post by sns2 on 2016-03-14
> **montag dp said:**
> I don't know.  I would have suggested xrandr --output HDMI1 --off to turn it off, and then xrandr --output HDMI1 --auto to turn it back on, but whatever works!  Sometimes the displays work in mysterious ways...

Thanks.. unfortunately, same problem, it did not help.   

I went to turn on the TV this morning, and, as usual, I only get the black screen.

So then I pressed my keyboard trigger for "xrandr --output HDMI1 --auto" and it still does nothing, same black screen.

So nothing has changed.  Every morning I still have to ssh in and sudo reboot it in order to restore the screen to working....

---

### Post by sns2 on 2016-03-14
> **mastablasta said:**
> have you tried something like mythbuntu or openelec if this is a media center?

if this is a Workstation then you should see how tv is recognised. it lok like the TV sends "off" signal to output and then it stays on off.

for example RaspberryPi i use for media center would dim the screen after some time. when i turn it on it would sometimes not react and wake up. turns out it have to give the TV (an LG LCD) a signal (with remote) that a HDD device is pluged in. once i do that remote activates the Pi and wakes it up from dimmed state. so perhaps in your case the TV needs to give it a kick.

This is a workstation/htpc  By that I mean its primary purpose is to run mythtv / kodi, but its running standard Ubuntu 14.04 LTS so that I can also surf the web, run a NAS, etc..  It's only display is the TV.

I don't quite understand what you are suggesting, I think you are suggesting I press something my TV remote.  

My sense is that Ubuntu is trying to be too clever.  I want Ubuntu to not care whether my TV goes on or off, just keep sending the same signal to the TV while it is off as when it is on.

I know there is something called an EDID that the TV sends while it is on.   I suspect the lack of EDID is causing the TV to not come back on once the TV has been off for a while.

---

### Post by montag dp on 2016-03-14
> **sns2 said:**
> Thanks.. unfortunately, same problem, it did not help.   

I went to turn on the TV this morning, and, as usual, I only get the black screen.

So then I pressed my keyboard trigger for "xrandr --output HDMI1 --auto" and it still does nothing, same black screen.

So nothing has changed.  Every morning I still have to ssh in and sudo reboot it in order to restore the screen to working....Are you using xrandr --output HDMI1 --off before turning off the TV?  I ask because you said before that when you did this, the next time you turned it on the screen was blue, not black.  When it is *blue*, that is when I would expect xrandr --output HDMI1 --auto to work to enable it again.

I think the problem is that simply turning off the TV confuses the Xorg, but using xrandr --output HDMI1 --off will disconnect it "gracefully." Correct me if I misunderstood you, but it sounds like you are just turning off the power, not running xrandr --output HDMI1 --off.

---

### Post by mastablasta on 2016-03-15
> **sns2 said:**
> 
I don't quite understand what you are suggesting, I think you are suggesting I press something my TV remote.  


yes. I have an option where I need to select HDD storage on tv menu with remote to be able to activate the PC.

I was doing the same thing before that (ssh+reboot).

on LG this button is called "Simplink"


> 
I know there is something called an EDID that the TV sends while it is on.   I suspect the lack of EDID is causing the TV to not come back on once the TV has been off for a while.

yes, this is very likely the case here.

---

### Post by sns2 on 2016-03-16
> **montag dp said:**
> Are you using xrandr --output HDMI1 --off before turning off the TV? I ask because you said before that when you did this, the next time you turned it on the screen was blue, not black. When it is *blue*, that is when I would expect xrandr --output HDMI1 --auto to work to enable it again.

I think the problem is that simply turning off the TV confuses the Xorg, but using xrandr --output HDMI1 --off will disconnect it "gracefully." Correct me if I misunderstood you, but it sounds like you are just turning off the power, not running xrandr --output HDMI1 --off.

hey montag,

thank you.  i think it is all working now with your suggestion.  originally i had thought that doing the '--off' was not working correctly, but it is now.

in fact, at the moment, i don't even seem to need to do the '--auto' when i turn it back on.  it comes on on its own, as long as i turned it "--off" beforehand, like you originally said.

thanks for the help

---

### Post by sns2 on 2016-03-16
ok, thanks.  montag's method is working out for me

---

### Post by montag dp on 2016-03-17
Awesome. Glad to hear it's working out for you now.

---

### Post by sns2 on 2016-03-27
Hi again,

Just want to follow up on this.

This technique seems to always work as far as getting the TV working.  In other words, it always gets me out of black screen mode.

However---  there are some fairly serious issues I am having with it.

Half the time, it works perfectly.  

The other half of the time, when the TV turns back on, I am surprised and annoyed to find that inexplicably any apps that had a running window left open on the screen have been killed, and the screen is now open to the Ubuntu login window.  I must enter my password, and I am back at an empty desktop with nothing running.  Note I do not require a password for login.

Has anyone experienced this?

---

