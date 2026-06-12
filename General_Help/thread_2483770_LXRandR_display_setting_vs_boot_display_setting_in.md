---
title: "LXRandR display setting vs boot display setting in LXQT with hdmi cable attached"
date: 2023-02-08
forum: General Help
---

### Post by xinuzi on 2023-02-08
**Situation:**

- hdmi cable is attached to desktop system and to external screen but you only want the desktop display on your pc after booting,
- in LXRandR screen preferences display is set to 'Only desktop',
- hdmi display is set to off in /home/user/.config/autostart/lxrandr-autostart.desktop,
- after boot desktop background has the wrong resolution (of the hdmi) anyway.
[B]
Solution:[/B]

No need for special startup script.

Go to:

Menu -> Preferences -> LXQT settings -> Monitor settings.

Set hdmi 'Enable this display' to **off**.

After boot your desktop background resolution should be fine, even with the hdmi cable attached.

You can enable the external screen (e.g. a tv) in the LXRandR-program afterwards when you want to use it.
Preferably with the same display resolution setting as on your desktop.

Greetz.

---

### Post by TheFu on 2023-02-08
And?

---

### Post by guiverc on 2023-02-08
[https://packages.ubuntu.com/kinetic/lxrandr](https://packages.ubuntu.com/kinetic/lxrandr)

Lxrandr is a *deprecated *GTK2 app intended for use with LXDE, and not Lubuntu/LXQt.  It's use doesn't strike me as efficient (*resource wise*), which is why it's not included on a *modern* Lubuntu install (*or last nine releases*).  LXQt uses `lxqt-config-monitor` for configuring monitors (*which you do mention*).

---

### Post by TheFu on 2023-02-08
Lxrandr is the easiest of the generic X resolution tools to use quickly. 'arandr' is another, but I'm used to typing lxrandr and that interface is very simple, clear, useful.  Not really interested in Qt-based tools, but I completely understand why LXQt wouldn't continue maintaining lxrandr, since they switched to Qt.

A simple, standalone, GUI like lxrandr would be very useful, without any toolkit connection.  Lots of people don't use DEs.

---

### Post by guiverc on 2023-02-08
> **TheFu said:**
> Lxrandr is the easiest of the generic X resolution tools to use quickly. 'arandr' is another, but I'm used to typing lxrandr and that interface is very simple, clear, useful.   ...
A simple, standalone, GUI like lxrandr would be very useful, without any toolkit connection.  Lots of people don't use DEs.

I very much :P (smiled) when I read *"simple, clear useful*"... as I had to stop myself using it.   (*I caught myself **twice****referring to LXDE tools in modern Lubuntu/LXQt support queries... I kept forgetting my primary desktop was a 17.10 install that was release-upgraded every 6 months, meaning I had some old [LXDE] stuff still installed*).

Yeah I like some WMs, though tend to use them mostly on *really old* hardware..

---

### Post by TheFu on 2023-02-08
> **guiverc said:**
> Yeah I like some WMs, though tend to use them mostly on *really old* hardware..

I dislike change and bloat, so I'm back to using fvwm on my desktops.  Gotta say, my Ryzen 6-core systems fly with fvwm and there's little worry about low RAM conditions.. ;)

lxrandr really is the quickest, easiest, tool that I know to make good settings for a presentation using a projector while in front of 10-250 people.

---

### Post by guiverc on 2023-02-09
And I have to admit that `arandr` helped save what little '*sanity*' I have left today...

( We have an issue with `lxqt-config` in (Lubuntu) *lunar* that meant my monitor.config didn't load when I logged in this morning... I used the system for awhile today, but reached my *limit* & used `arandr` to quickly *bypass* the issue.. I also considered logging out & using ICEwm, esp. on your "*lots of people don't use WMs*" comment )

---

### Post by TheFu on 2023-02-09
I cheat on my desktops. Since the monitors don't change much (maybe once every decade), I just setup 1 modeline in my custom xorg with the resolution I want for that screen.  Then I never need worry about the wrong one being picked unless something really bad happens, usually with nvidia drivers.

---

### Post by guiverc on 2023-02-09
> **TheFu said:**
> I cheat on my desktops. Since the monitors don't change much (maybe once every decade)

:P  

I'm the same (*rarely change my hardware*), but keeping my system as default as possible allows me to detect when something goes wrong (*like my monitor arrangement no longer working*!) which is what had me resort to using `arandr` to fix....

That problem has been fixed now (*change came through late yesterday for me*), but that's a lot of why I'm actually using *lunar*; to detect issues & report when they happen.

---

### Post by xinuzi on 2023-02-10
Have (quickly, with hardly variables) written a script anyway which toggles between tv and pc. Connected by hdmi-cable.
Whenever the hdmi/tv is activated the sound goes with it (IN MY CONFIGURATION).
Have used 'xrandr' for the screen-settings.
All you need is the buttons 1, 2 and 3 ;-)
Check your own screen and sound settings. Especially the screen TV and PC should correspond (in this case: 1366x768).
For the sound, do a cli 'pactl list' command and look for 'Card nr' and 'Profile'.
(Hopefully no mistakes as I've translated the script from my mothertongue. Improvements always welcome.)

Full script:

```
#!/bin/bash

clear

TITLE="HDMI VS PC ON/OFF"
echo -en "\033]0;$TITLE\a" # Window title

echo "$TITLE"

echo

sel (){ 

COLUMNS=12 # items always under each other in one column
select CHOICE in "HDMI ON - PC ON" "HDMI ON - PC OFF" "HDMI OFF - PC ON" 
do
echo "Your choice: $REPLY"
if [[ $REPLY > $CHOICE ]]
then
echo "Wrong choice!"

elif [[ $CHOICE == "HDMI ON - PC ON" ]] 
then

xrandr --output HDMI-0 --mode 1366x768 --rate 60.00 --output LVDS --mode 1366x768 --rate 60.00
sleep 1
pactl set-card-profile 0 output:hdmi-stereo
sleep 1
pactl set-card-profile 2 output:analog-stereo+input:analog-stereo # = stereo duplex (random stereo = 'output:analog-stereo')
echo
echo "HDMI = ON, PC = ON."

elif [[ $CHOICE == "HDMI ON - PC OFF" ]]
then

xrandr --output HDMI-0 --mode 1366x768 --rate 60.00 --output LVDS --off
sleep 1
pactl set-card-profile 0 output:hdmi-stereo
sleep 1
pactl set-card-profile 2 off
echo
echo "HDMI = ON, PC = OFF."

elif [[ $CHOICE == "HDMI OFF - PC ON" ]]
then

xrandr --output HDMI-0 --off --output LVDS --mode 1366x768 --rate 60.00
sleep 1
pactl set-card-profile 0 off
sleep 1
pactl set-card-profile 2 output:analog-stereo+input:analog-stereo # = stereo duplex (randum stereo = 'output:analog-stereo')
echo
echo "HDMI = OFF, PC = ON."

fi
break
done
}

sel

echo

echo "Enter = Restart"
echo "Ctrl+c or 'Close'-button = Close Window"

read

exec bash "$0" "$@" # Reload this script
```

---

