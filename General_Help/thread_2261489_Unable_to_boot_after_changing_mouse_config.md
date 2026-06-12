---
title: "Unable to boot after changing mouse config"
date: 2015-01-19
forum: General Help
---

### Post by eliminate1337 on 2015-01-19
I have a RAT 7 mouse and it doesn't work on linux without changing some config files. It has some kind of glitch with a specific button being registered as pressed all the time and I googled a fix.

I put this code in a config file
```
Section “InputClass”
Identifier “R.A.T.”
MatchProduct “Saitek Cyborg R.A.T.7 Mouse&#8243;
MatchDevicePath “/dev/input/event*”
Option “Buttons” “17”
Option “ButtonMapping” “1 2 3 4 5 0 0 8 9 7 6 12 0 0 0 16 17&#8243;
Option “AutoReleaseButtons” “13 14 15&#8243;
Option “ZAxisMapping” “4 5 6 7&#8243;
EndSection

```

I moved that file to /usr/share/X11/xorg.conf.d. After doing that I was unable to boot. It gets stuck on a blank console window with no error messages or anything like that. I'm able to boot into the console and delete the config file manually and it works fine. Does anyone know a fix, both for the mouse and for the booting problem?

---

### Post by Toz on 2015-01-20
The open and close quotes don't look right. What program did you use to create that file?

/var/log/xorg.0.log.old might have some information about what went wrong (assuming the last boot attempt was the problem one).

Try copying/pasting this version into the file:
```
Section "InputClass"
	Identifier "R.A.T."
	MatchProduct "Saitek Cyborg R.A.T.7 Mouse"
	MatchDevicePath "/dev/input/event*"
	Option "Buttons" "17"
	Option "ButtonMapping" "1 2 3 4 5 0 0 8 9 7 6 12 0 0 0 16 17"
	Option "AutoReleaseButtons" "13 14 15"
	Option "ZAxisMapping" "4 5 6 7"
EndSection
```
...using an editor like mousepad.

---

### Post by eliminate1337 on 2015-01-20
Someone on these forums somewhere said to use that. I used mousepad. I'll try what you said.

---

### Post by Toz on 2015-01-20
If it doesn't work, on next reboot, look at the file /var/log/xorg.0.log.old for hints as to what went wrong.

---

