---
title: "ubuntu 13.10 - how to start/bootup with sound ON"
date: 2013-11-30
forum: General Help
---

### Post by Bushcraft Bill on 2013-11-30
I have to manually turn on the sound on every time I startup ubuntu is their code I can put in somewhere that will turn on the sound for me automaticly on bootup of ubuntu 13.10 

Thanks
Bill

---

### Post by germanix on 2013-11-30
Have you checked the settings in "system settings" then "sound" then the tab "output" and the slider at the bottom "output volume" is set to 100% ? Also check the tab "sound effects" if it is activated and the volume turned up if you require the sound effects. You can also check under start-up programs if the volume is activated to start at start-up.

---

### Post by isabelgobbo on 2013-12-01
I think you need to have a entry in startup applications.

Name: Pulse Audio System Sound;
Command: ```
start-pulseaudio-x11
```
Comment:  Start System Pulse Audio Sound

I don have sure if the right name it's startup application because may Ubuntu 13.10 it's portuguese from Brazil.

---

### Post by Bushcraft Bill on 2013-12-02
that did not work for me it still loads with sound turned down to 0 was hopeing their would be a way to get sound turned up on bootup I know their must be a way to fix this their is always a fix for ubuntu!

---

### Post by Bushcraft Bill on 2013-12-04
you know it finally dawns on me that the sound problem started right after I added my HDMI monitor so their must be some kind of bug in the system that does not like the HDMI monitor.... but still should be a fix to crank up the volume on ubuntu 13.10 startup... I just cant seem to find the fix though anyone have a clue what I can try?

---

