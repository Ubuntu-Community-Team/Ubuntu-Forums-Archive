---
title: "Screen goes black after 10 min, no matter what I do... Ubuntu 13.04"
date: 2013-11-21
forum: General Help
---

### Post by Halpm on 2013-11-21
My screen goes blank after exactly 10 minutes. Always. With Gnome screensaver, xscreensaver, no screensaver installed, or whatever. 10:00: blank screen. Sometimes even when I'm in the middle of something.
I don't really know where to start, and all info I can find on the subject is about earlier version s of Ubuntu, and refer to files that don't seem to exist anymore.
Any ideas?

---

### Post by stinkeye on 2013-11-21
Try...
```
xset -dpms
```
 
I use this toggle script.
Not mine...came across it somewhere. 
It incorporates the xset command with power settings.

_screen-blanking-toggle.sh_
```
#!/bin/bash

# This script automatically changes power settings, so that the screen will
# not turn off and the computer will not suspend e.g. when user wants to watch
# video.  


# Input argument: 'off' or 'on'.  If no input argument is specified, then
# will toggle power saving mode - the opposite of the current setting.


################################################################################
### Settings


# Idle time until turning off the screen (seconds)
# Only use one setting here because GUI version only has one
sleep_time=300


# Idle time until suspending (seconds) (0 means never)
suspend_bat=300
suspend_ac=0


################################################################################


# Path in gsettings
gsetpath=org.gnome.settings-daemon.plugins.power
gsetpath1=org.gnome.desktop.session


# Check value for screen turnoff
cur_sleep_bat=`gsettings get $gsetpath sleep-display-battery`
cur_sleep_ac=`gsettings get $gsetpath sleep-display-ac`


toggle=$1


# Determine whether to switch on or off
if [[ "$toggle" == '-off' || "$toggle" == "-OFF" || "$toggle" == "-Off" ]]; then
  switch='off'
elif [[ "$toggle" == '-on' || "$toggle" == "-ON" || "$toggle" == "-On" ]]; then
  switch='on'
else
  echo
  echo "-on or -off not specified: will toggle power savings mode."
  if [[ $cur_sleep_bat -gt 0 || $cur_sleep_ac -gt 0 ]]; then
    switch='off'
  else
    switch='on'
  fi
fi


# Toggle power saving on or off
echo 
if [ "$switch" == 'off' ]; then


  echo "Switching off power saving mode"
  notify-send -i video-display "Screensaver OFF"
  xset -dpms
  #echo "Screensaver OFF" > ~/.ss-status.txt


# Time until screen turns off (0 is never)
  gsettings set $gsetpath sleep-display-ac 0
  gsettings set $gsetpath sleep-display-battery 0 


# Time until suspend (0 is never)
  gsettings set $gsetpath sleep-inactive-ac-timeout 0
  gsettings set $gsetpath sleep-inactive-battery-timeout 0


# Turn off dimming of screen
  gsettings set $gsetpath1 idle-delay 0
  gsettings set $gsetpath idle-dim-ac "false"
  gsettings set $gsetpath idle-dim-battery "false"


else


  echo "Switching on power saving mode"
  notify-send -i video-display "Screensaver ON"
  xset +dpms
  #echo "Screensaver ON" > ~/.ss-status.txt


# Time until screen turns off (0 is never)
  gsettings set $gsetpath sleep-display-ac $sleep_time
  gsettings set $gsetpath sleep-display-battery $sleep_time 


# Time until suspend (0 is never)
  gsettings set $gsetpath sleep-inactive-ac-timeout $suspend_ac
  gsettings set $gsetpath sleep-inactive-battery-timeout $suspend_bat


# Turn on dimming of screen
  gsettings set $gsetpath1 idle-delay $sleep_time
  gsettings set $gsetpath idle-dim-ac "true"
  gsettings set $gsetpath idle-dim-battery "true"


fi
echo
```

---

### Post by Halpm on 2013-11-21
As far as I can see, the [COLOR=#000000][FONT=Ubuntu Mono]xset -dpms command makes no difference. Still a blank screen after 10 minutes. It doesn't have to be root by any chance does it?[/FONT][/COLOR]

---

### Post by stinkeye on 2013-11-21
Like you I came across many different solutions usually involving some xset command.
The script works for me....maybe try caffeine...
```
sudo apt-add-repository ppa:caffeine-developers/ppa
sudo apt-get update
sudo apt-get install caffeine
```

---

### Post by vasa1 on 2013-11-21
> **Halpm said:**
> ... Sometimes even when I'm in the middle of something. ...
What do you mean by *in the middle of something*? What is *something*? Does it involve keyboard or mouse activity?

I use this code as an autostart script to prevent blanking:
```
#!/usr/bin/env bash

sleep_period=8m

while true; do
  highest_cpu="$(ps -eo %C --sort -%cpu | awk 'NR==2 {print $1}')"
  if [[ "$highest_cpu" > 3.0 ]];then
      notify-send 'CPU alert!' "$highest_cpu"
      xdotool key shift
  fi
  sleep ${sleep_period}
done
```
The "notify-send" line isn't essential. And **xdotool** has to be installed.

---

### Post by Halpm on 2013-11-22
By in the middle of something I mean that I can be surfing the net, or actively typing away on a document, and the screen may turn black after what seems like 10 minutes. Caffeine seems to be helping, but only when the laptop is plugged in? Haven't quite found the pattern yet...

---

### Post by Halpm on 2013-11-23
It's weird. Installing caffeine seems to have "mostly" fixed the problem. It blanks out after ten minutes maybe one in ten boots now, and then doesn't do it after a reboot. Perhaps slightly more often on battery than when plugged in?
Odd. Very odd - but don't ya just love ubuntu?

---

### Post by Halpm on 2013-11-24
Ok - this is a bit odd... After turning the machine off, taking out the battery and leaving it for an hour, the issue seems to have gone entirely. Laptops are black magic. I'm going to give this a couple of days, then mark as solved...

---

### Post by Halpm on 2013-11-24
Nope - false alarm.

---

### Post by dave35 on 2013-11-24
It maybe the settings in your monitor ..

Sorry, didn't see a reference to a laptop in the first post ...

---

### Post by Halpm on 2013-11-24
I've found a pattern:
Some times, when I boot up, the splash screen doesn't show and I get this error message very quickly - I had to film it with my camera to catch it:
acpi_call: cannot get handle: Error: AE_NOT_FOUND
When that happens, then I get the problem with the screen turning off every ten minutes.
When it boots up properly, and shows the splash screen, then I don't get the problem - even now that I've disabled Caffeine.

---

### Post by Halpm on 2013-11-28
Marking this as solved, not because it is, but because I've changed over to ubuntu studio for other reasons.

---

