---
title: "Error starting the GNOME Settings Deamon"
date: 2006-11-04
forum: General Help
---

### Post by johnny9794 on 2006-11-04
ATM i am running edgy off of live cd and apon start i got an error. screenshot below.


i get the same error even if i load up the live dvd of ubuntu edgy 6.10

Has anybody run accross this problem? 
Any solutions?

Thanx.

[edited]
Sorry never mind i restarted it 3 times and finally it booted up fine...

---

### Post by m47h3us on 2006-11-07
i got the same error but dont no how it has started i need it sorting too

---

### Post by strabes on 2006-11-07
try killall gnome-settings-daemon and then starting it again. you can also set it to startup with gnome with gnome-session-properties

Just open a terminal window (or alt+f2) and run ```
killall gnome-settings-daemon
```
Then hit alt+f2 and type in "gnome-settings-daemon" to start it again. The reason you should use alt+f2 to start it is so that if you close the terminal window gnome-settings daemon won't exit. If you really wanted to run it through terminal you could just put an ampersand (&) after it like this: ```
gnome-settings-daemon &
```

Then it would run in the background, you could close the terminal window and it would continue running.

---

### Post by stooshbunutu on 2008-02-23
thanks for that, would thank but no button on this older post

---

### Post by TolgaYazicioglu on 2008-03-11
I tried the code but it didn't worked
it gives this error every time.  I tried to reinstall the gnome settings daemon but don't worked

the terminal answer for killing and opening gnome settings

tolga@tolga-laptop:~$ killall gnome-settings-daemon
gnome-settings-daemon: no process killed
tolga@tolga-laptop:~$ gnome-settings-daemon
Resource Timestamp: 38781
Resource Configuration Timestamp: 38781
CRTC 49 Timestamp: 38781
CRTC 4a Timestamp: 38781
Output 4b Timestamp: 38781
Segmentation fault (core dumped)
tolga@tolga-laptop:~$ 


what should i do

---

### Post by TolgaYazicioglu on 2008-03-11
[IMG]http://img391.imageshack.us/img391/9726/errorlk7.png[/IMG]

this is the error i get

---

