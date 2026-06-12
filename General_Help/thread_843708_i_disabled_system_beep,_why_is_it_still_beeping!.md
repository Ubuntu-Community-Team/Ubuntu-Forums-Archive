---
title: "i disabled system beep, why is it still beeping!?"
date: 2008-06-28
forum: General Help
---

### Post by eival on 2008-06-28
everytime i shutdown my laptop it beeps, even tho ive already went to System > Preferences > Sound > i turned off all system sounds and i unchecked "enable system beep"

why am i still hearing sounds, can someone tell me where i can uninstall the driver, i had this same issue with windows but i knew how to get to the driver an uninstall it, i dont know where to go in Ubuntu tho.


im using Hardy Haron 64 Bit


EDIT: also i still hear the drums sound when i get to the log-in screen, even tho(again) i have all system sounds turned off including the "Log In" screen sound set to "no sounds"

---

### Post by neoAnderson on 2008-06-28
Probably it is a hardware setting which you can disable from your BIOS. I have special keys on the first row of my laptop keyboard and they beep every time they are pressed; and for me, this can be disabled from the BIOS.

Check your BIOS settings.

EDIT: just saw the edit about the drum sounds - no idea why that happens...

---

### Post by lisati on 2008-06-28
> **eival said:**
> 
  also i still hear the drums sound when i get to the log-in screen, even tho(again) i have all system sounds turned off including the "Log In" screen sound set to "no sounds"

> **neoAnderson said:**
> just saw the edit about the drum sounds - no idea why that happens...

Similar problem(?) and possible solotuion: Are you systems correctly remembering the settings? On 7.04 I usually like my login screen to be a list of users on the machine. Sometimes when I've reset it to do so after a fresh install, it gets mysteriously changed to "random from selected". The workaround I've use is to put it back to "Selected them only", which fixes it. Maybe something similar is going on.

---

### Post by logos34 on 2008-06-28
I have a similar problem...keep hearing these blasted sound effects AFTER I disable every setting in sound prefs!

In my case, though, its not so much the startup/shutdown sounds or beeps that bug me as it is some of the other stuff

I've disabled system sounds and ESD server in sound prefs, and still I get that 'boink!' or whatever after every single file download from the internet!  It's really annoying when you're playing back music at the same time, as you can imagine. So basically how to allow music/audio and kill the effects crap?

---

### Post by scouser73 on 2008-06-29
Go to System > Preferences > Sound untick System beep, then click the Sounds tab and untick Play System Sounds. This should sort it for you.

---

### Post by BlueSkyNIS on 2008-06-29
I also find the System Preferences just too buggy. Sometimes is so stubborn and wont change a sound so I need to logout and login back just to see the change I made. At the moment I'm too lazy to fill a bug...

---

### Post by Victormd on 2008-07-02
For the system beep, you can blacklist it so it won't start up anymore:
```
sudo gedit /etc/modprobe.d/blacklist
```
and add the following to the end of the file:
```
blacklist pcspkr
```
To remove it for this session:
```
sudo rmmod pcspkr
```

---

