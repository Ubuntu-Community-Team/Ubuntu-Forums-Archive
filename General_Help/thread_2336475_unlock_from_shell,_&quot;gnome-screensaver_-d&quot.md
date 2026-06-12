---
title: "unlock from shell, &quot;gnome-screensaver -d&quot; not working"
date: 2016-09-08
forum: General Help
---

### Post by herkules on 2016-09-08
I'd need some help to unlock my ubuntu 16.04 with a shell command.

The profane 'usecase': I have written a small alarm-clock program (python) to play some music and light up the screen (so I have light when I wake up...) and show some other stuff like weather.

I used to manage the unlock with the command: gnome-screensaver -d . This used to work with my old installation (also ubuntu 16.4 but upgraded there from many times back) but does not work with my fresh install. (I also tried DISPLAY=:0 gnome-screensaver-command -d   but no luck either).

Interestingly enough I can lock the screen with gnome-screensaver-command -l  

Any ideas? Any hints are appreciated!

Ulrich

---

### Post by CantankRus on 2016-09-08
Testing here the command **gnome-screensaver-command --deactivate** only works when locking of the screen is disabled.
[ATTACH=CONFIG]271035[/ATTACH]
Test...
```
gnome-screensaver-command --activate && sleep 15 && gnome-screensaver-command --deactivate
```


When the lockscreen is enabled I can send a keystroke using **xdotool **which deactivates the screen blanking to show the lock screen. 
eg testing...
```
gnome-screensaver-command --activate && sleep 15 && xdotool key shift
```

---

### Post by herkules on 2016-09-09
Hi,

Thanks for your reply!

You are right - The problem is the lock screen, not the screensaver.

Do you have any clue how I can pass the lockscreen?

---

### Post by CantankRus on 2016-09-09
When the lock screen is active and the screen is blanked you can unblank and unlock
by sending your password using something like xdotool.

test eg
```
gnome-screensaver-command --activate && sleep 15 && xdotool key --delay 50 [COLOR="#FF0000"]P A S S W O R D[/COLOR] Return
```
where [COLOR="#FF0000"]P A S S W O R D[/COLOR] is your password separated by spaces.

For added security I would store my password in the GNOME keyring and use a python module to access the keyring. eg [**_[COLOR="#B22222"]keyring 9.3.1[/COLOR]_**]("https://pypi.python.org/pypi/keyring")
I'm just an amateur bash scripter but as you mentioned you wrote the script in python I'm sure you could write something using python.
I use [**_[COLOR="#B22222"]gkeyring.py[/COLOR]_**]("https://github.com/kparal/gkeyring") to give me shell access to GNOME keyring as outlined [**_[COLOR="#B22222"]HERE[/COLOR]_**]("https://ubuntuforums.org/showthread.php?t=2125918")

---

### Post by herkules on 2016-09-10
Thanks for the hint!

I really didn't want to have my password lying around in the code - the access to the keyring solves this

Thanks again

---

