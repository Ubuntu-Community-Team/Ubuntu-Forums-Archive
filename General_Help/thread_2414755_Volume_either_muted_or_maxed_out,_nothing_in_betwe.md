---
title: "Volume either muted or maxed out, nothing in between"
date: 2019-03-14
forum: General Help
---

### Post by derfreddie on 2019-03-14
Thank you for clicking by! This is my first post here.

I recently installed Ubuntu 18.10 on my ASUS ZenBook Pro UX550VE laptop, replacing Windows, and I am very happy with it over all.

The only problem I have is with the sound. I am able to change the volume, either with the software controls, or the buttons on the keyboard, but as long as the volume is not turned all the way down to mute, it only plays at max volume, which is very inconvenient. Right now, the only way I can reduce the volume, is by reducing it in the program currently making sound (Spotify, YouTube, etc.), which I do not consider a good solution, partly because it does not affect anything but that one program itself.

The problem, however, does not occur when using bluetooth headset. Then I am able to adjust the system volume just as normal.

It was like this while using the live-CD to test out Ubuntu the first time, during the installation process, right after the installation, and now. I have tried installing some sort of audio drivers, but these just introduced new problems or didn't work at all.

Has anyone else similar problems? Thank you very much!

---

### Post by TheFu on 2019-03-14
I run 16.04 with a limited GUI on an Asus F510UA.  To get the volume keys working, I remapped then using the window manager settings. My WM is openbox. Openbox uses an XML config file in ~/.config/openbox/
```

<keybind key="W-F10"><action name="Execute"><command>pactl set-sink-volume 0 0% </command></action></keybind>
<keybind key="W-F11"><action name="Execute"><command>pactl set-sink-volume 0 -10%</command></action></keybind>
<keybind key="W-F12"><action name="Execute"><command>pactl set-sink-volume 0 +10%</command></action></keybind>
```

These set the mute, vol-dn, vol-up, keys to work using the "super-F10" key, etc.  As you can see, the actual commands used are tied to pulse audio and "sink 0".  The mute doesn't toggle back on, just mutes.

My system is highly customized since I don't use any normal GUI. I do remember that with Ubuntu-Mate, the audio controls did work.

I did some mapping to get the screen brightness keys working too.```

<keybind key="W-F5"><action name="Execute"><command>xbacklight -dec 10</command></action></keybind>
<keybind key="W-F6"><action name="Execute"><command>xbacklight -inc 10</command></action></keybind>
```
On my previous laptop, xbacklight didn't work, so this is a good improvement.

---

### Post by derfreddie on 2019-03-14
My problem is not with the keybindings or being able to access the volume controls. I can press the f11 and f12 keys just fine and the volume slider adjusts acordingly on the screen. The problem is: even though the slider is set to 10% or whatever, all sounds play at 100%. The only way I can make it not play at 100%, is by turning the volume controls built into applications (like Spotify, YouTube, etc.) almost all the way down.

---

### Post by CatKiller on 2019-03-14
It sounds like PulseAudio has picked up the wrong mixer to control the volume on your sound device. You could play around with alsamixer to identify which one it should be using, and then look for a way to configure pulse to use that instead of whichever one it's using now.

---

### Post by derfreddie on 2019-03-14
I was able to find a solution! Posting it here in case someone else has the same problem.

I opened ***alsamixer ***in the terminal and discovered that the volume was depending on the PCM value there, not the master value.

By opening this...
```
sudo nano /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
```

...locating this section...
```
[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right
```

...adding these lines _before_ it...
```
[Element Master]
switch = mute
volume = ignore
```


...and rebooting the computer, the problem was solved.
Thank you for the help!

---

### Post by TheFu on 2019-03-14
Thanks for posting the solution.

Marking this thread as "solved" using the "thread tools" button near the top would really help the community.

---

