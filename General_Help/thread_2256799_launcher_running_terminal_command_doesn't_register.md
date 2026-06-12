---
title: "launcher running terminal command doesn't register in terminal"
date: 2014-12-14
forum: General Help
---

### Post by tcll5850 on 2014-12-14
here's the launcher, or launchers:

```
[Desktop Entry]Version=1.0
Type=Application
Name=game
Comment=Enable Line-In playback
Exec=pactl load-module module-loopback latency_msec=1
Icon=applications-games-symbolic
Terminal=true
StartupNotify=false
```

```
[Desktop Entry]Version=1.0
Type=Application
Name=Mic
Comment=Disable Mic playback-echo
Exec=pactl unload-module module-loopback
Icon=audio-input-microphone-symbolic
Terminal=true
StartupNotify=false
```

those commands work perfectly while running the terminal, but when clicking  the launcher, the terminal window just appears then closes with no action.

how can I get these to work??
thanks :)

---

### Post by mc4man on 2014-12-14
Works fine here though you don't need a terminal=true in the .desktop. 
What doesn't work is what you posted, the Version=1.0 is on top line, it can't be there (or typo on you?
Ex. of fine here, didn't bother with icon, it's a non-factor - 
```
[Desktop Entry]
Version=1.0
Type=Application
Name=game
Comment=Enable Line-In playback
Exec=pactl unload-module module-loopback
Icon=
Terminal=
StartupNotify=false
```

If the wrong line 1 isn't your problem post back that.

(- The whole deal could also be done as a single .desktop. The Exec= would run a script that enables if disabled, disables if enabled. 
You could have a notification of action taken.

---

### Post by tcll5850 on 2014-12-14
... yea that's a typo that went unnoticed ._.
I copied that from notepad, and it's not like that there

but yea, I'm using XFCE and have launchers (creates new desktop files) in the bottom bar next to my clock.

ironicly enough (I literally did nothing but get on Minecraft for a few hours) the buttons work now.
... ok then...

thanks for trying :)

---

