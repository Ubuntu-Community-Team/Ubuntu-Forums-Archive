---
title: "Who blanks my screen?! HELP!"
date: 2008-01-15
forum: General Help
---

### Post by barduck on 2008-01-15
Hello All,

I have an old IBM Thinkpad 600x laptop that I intend to turn into a digital picture frame. I used the Alternative Ubuntu CD and installed a bare system with only the base packages and then used APT-GET to install X server and the FEH image viewer.

Then I prepared a bunch of scripts that are supposed to run the FEH viewer when the computer starts. The slideshow script just starts FEH in full screen with the slideshow parameter and pictures directory.

```
killall feh unclutter
unclutter &
feh -zZFr -D 3 /var/pics
```

Then I have a script that disables screen blanking and calls xinit with the slideshow:

```
setterm -blank 0
/usr/bin/X11/xinit /usr/local/bin/slideshow.sh &
```

And then I have */etc/init.d/picframe [start/stop/restart]* that calls the script above.Now I added a sym link in */etc/rc3.d/S99picframe* that points to */etc/init.d/picframe*. All is nice and working as expected, when I restart the machine X server starts and the slideshow runs.

All fine until the screen gets blank after exactly one hour and this is, of course, not something you would want in a picture frame. I looked everywhere and tried everything that was suggested but I still can't get rid of the screen blanking.

I have the following to */etc/X11/xorg.conf*:

```
Section "ServerFlags"
        Option "DPMS"   "0"
        Option "BlankTime" "0"
        Option "StandbyTime" "0"
        Option "SuspendTime" "0"
        Option "OffTime" "0"
EndSection

```

This is the output I get from *xset -display :0 -q* while the image viewer is running:

```
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfe5ef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log

```

What turns my screen blank? Is it X server? The terminal? Something else? Please help.

Thanks!

- barduck

---

### Post by Max_rulez on 2008-01-15
i think your delay might be a bit long

---

### Post by barduck on 2008-01-15
> **Max_rulez said:**
> i think your delay might be a bit long

What do you mean? What delay?

---

### Post by barduck on 2008-01-15
Ok, an update:

I removed the xinit and the viewer line from the script and rebooted so X server will not start. So now it just boots and sits there at the console with the login prompt. So I didn't touch anything and after exactly one hour, the screen turns blank again.

So it isn't X server that blanking it, right?

What else can it be? I thought that once X runs, it is in control of the display?

Any ideas?

- barduck

---

### Post by blueorder on 2008-01-15
> **barduck said:**
> Ok, an update:

I removed the xinit and the viewer line from the script and rebooted so X server will not start. So now it just boots and sits there at the console with the login prompt. So I didn't touch anything and after exactly one hour, the screen turns blank again.

So it isn't X server that blanking it, right?

What else can it be? I thought that once X runs, it is in control of the display?

Any ideas?

- barduck

Try looking in:

```
/etc/console-tools/config
```

and change the BLANK_TIME

This is the info that accompanies BLANK_TIME:

```
# screen blanking timeout.  monitor remains on, but the screen is cleared to
# range: 0-60 min (0==never)  kernels I've looked at default to 10 minutes.
# (see linux/drivers/char/console.c)

```

I have a server that has only command line and it blanks out after a period of time. This might be your culprit right there.

**EDIT:**

Also, take a loot at POWERDOWN_TIME

```
# Powerdown time.  The console will go to DPMS Off mode POWERDOWN_TIME
# minutes _after_ blanking.  (POWERDOWN_TIME + BLANK_TIME after the last input)
POWERDOWN_TIME=30
```

**EDIT 2:**

Changing powerdown_time might not be necessary since it only does it after blank_time and if blank_time never happens it might never go into powerdown_time. Don't know for sure. Test both ways.

---

### Post by ErebusBat on 2008-01-15
I would also check your BIOS. I have a couple of old laptops where the BIOS will blank the screen to save on energy consumption. Worth a shot.

---

### Post by barduck on 2008-01-16
> **ErebusBat said:**
> I would also check your BIOS. I have a couple of old laptops where the BIOS will blank the screen to save on energy consumption. Worth a shot.

Nope, there is nothing in the BIOS that mentions any power saving or screen blanking. Thanks.

---

### Post by barduck on 2008-01-16
Thank you blueorder for your ideas, I checked these values (BLANK_TIME and POWERDOWN_TIME) and they were both set to 30 minutes so I guess this was not it. Just in case I set them both to 0.

The problem still persists.

Anything else I can try?

- barduck

---

### Post by Max_rulez on 2008-01-16
i know go system, Preferences, screensaver and turn it all off

---

### Post by Max_rulez on 2008-01-16
or try power management change both of them to never

---

### Post by barduck on 2008-01-16
> **Max_rulez said:**
> i know go system, Preferences, screensaver and turn it all off

I know you are just trying to help and appreciate it but did you really read my question?

I don't have gnome or power management applets. Why would I go digging in configuration files and come here asking for help if it was as easy as setting some preferences from a menu?

---

### Post by barduck on 2008-01-17
I found out that this issue may not be caused by Linux. 


I booted the laptop into the Ultimate Boot CD and selected FreeDos boot. Left the machine untouched and...you guessed it, it blanks the screen exactly after one hour.

So this might be a BIOS issue but there is no option anywhere in the BIOS settings that even remotely mentions power management, blank screen or standby mode.


There must be some way to control and disable this from Linux, still need your help...

- barduck

---

### Post by barduck on 2008-01-22
I am still hoping someone will notice this and have some wild idea that will shed the light on this issue...

---

### Post by TinkerJ on 2008-01-23
Perhaps an updated BIOS is available that adds that feature? Seems short-sighted of the manufacturer to have a permanent screen blanking timer.

---

### Post by barduck on 2008-01-24
> **TinkerJ said:**
> Perhaps an updated BIOS is available that adds that feature? Seems short-sighted of the manufacturer to have a permanent screen blanking timer.

It was already updated to the latest BIOS but it didn't change anything.

I tried this with Windows XP - disabled all power saving options and let it run and it didn't blank on Windows XP. This may hint that Windows XP knows how to disable this blanking. Maybe some drivers that Windows XP takes advantage of and Ubuntu and DOS don't?

In the meanwhile, someone on the thinkpads forums suggested to run a thinkpad configuration utility and see if it can be disabled from there, I have yet to try this idea.

- barduck

---

### Post by barduck on 2008-01-25
OK, problem solved! With the help of someone on the thinkpad forums.

For future reference, in the unlikely event of someone having a similar problem and finding this post -

The problem was in the thinkpad BIOS settings (which are not accessible through the normal BIOS config). I used thinkpad configuration utility for DOS (PS2.exe) to set the custom time for LCD blank to 0 and then set the power saving mode (PMODE parameter) to "Custom", instead of the default "HIGH".

Here go few hours of head scratching I will never get back but at least it works now and I learned something.

Thanks

- barduck

---

### Post by wigadore on 2008-03-25
@Barduck
Do you have a step by step tutorial as to how you put this project together. I have built one with DSL and honestly the hardware support for the hardware I have is not the greatest. I have a Thinkpad T30 and a few Dell D600/800 series laptops I would like to get ubuntu working on. Problem is I am a very new Linux user and I am not getting far fast. Thanks

---

### Post by pja on 2008-05-19
See [http://ubuntuforums.org/showthread.php?p=4993141#post4993141]("http://ubuntuforums.org/showthread.php?p=4993141#post4993141") for my solution to this problem based on this and other posts.

Regards,
Peter

---

