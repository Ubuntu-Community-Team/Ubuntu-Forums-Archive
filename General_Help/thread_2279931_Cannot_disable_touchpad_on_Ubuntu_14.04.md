---
title: "Cannot disable touchpad on Ubuntu 14.04"
date: 2015-05-26
forum: General Help
---

### Post by Juarez_Aires_Sampa on 2015-05-26
[COLOR=#141823][FONT=helvetica]Can someone provide an easy way to completely disable touchpad on Ub[/FONT][/COLOR][COLOR=#141823][FONT=helvetica]untu 14.04? Previously I was able to disable it on the settings menu, but now it won't let me. I'll disable it and it will enable again by itself. I've tried playing with xinputs but it didn't work. This is so annoying, I simple cannot type with the touchpad enabled. I've had this problem before, sometimes restarting would fix, but not even this now. My current solution is to tape around 20 sheets of paper on top of the touchpad. A hardware solution to this unnecessary software headache.

This is the output of xinput -list:
```
 Virtual core pointer                        id=2    [master pointer  (3)]&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0    id=11    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0    id=12    [slave  pointer  (2)]
&#9116;   &#8627; DLL063E:00 06CB:2934                        id=14    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® Nano Transceiver v2.0    id=10    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                        id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=17    [slave  keyboard (3)]



```

I am not sure which device to disable, I've tried:
[/FONT][/COLOR]xinput set-prop 2 "Device Enabled" 0
and

xinput set-prop 16 "Device Enabled" 0

The first one produces this error:
```
X Error of failed request:  BadAccess (attempt to access private resource denied)  Major opcode of failed request:  131 (XInputExtension)
  Minor opcode of failed request:  57 ()
  Serial number of failed request:  20
  Current serial number in output stream:  21



```
The second runs silently, but the touchpad still works.

---

### Post by pretty_whistle on 2015-05-26
I installed "Pointing devices" from the Software Center and it has "disable touchpad" in it.  This worked for me.

---

### Post by mc4man on 2015-05-26
It's a bug that has evolved for some time but never fixed - 
[https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1283863](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1283863)
So you just need to use some other method to keep it disabled, here I used to use a startup app but now use [touchpad-indicator]("https://launchpad.net/~atareao/+archive/ubuntu/atareao"). The above mentioned method would also likely work, point is to use something that works at or just after login.

(- For the startup app method I created a .desktop in .config/autostart like
```
mkdir -p ~/.config/autostart && gedit ~/.config/autostart/touchpad.desktop
```
then put this in, takes affect 3 sec after login, can be lowered to 2 or maybe 1,  though a delay is needed longterm..

```
[Desktop Entry]
Type=Application
Exec=gsettings set org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled false
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=No touchpad
X-GNOME-Autostart-Delay=3
```

---

