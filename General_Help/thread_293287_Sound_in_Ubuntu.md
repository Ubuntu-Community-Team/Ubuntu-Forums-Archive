---
title: "Sound in Ubuntu"
date: 2006-11-05
forum: General Help
---

### Post by insertwackynamehere on 2006-11-05
I recently installed Ubuntu 6.10, and I really like it. I was able to hear sounds (like the startup sound and all) without a problem, originally. Today I installed the nvidia drivers for linux and they work (I can get doom3 to run) but then I realized my sound was dead! The truth is, I had installed the nvidia drivers the night before and doom3 (and sound all worked) but when I tried again this morning, I had an X server error and I was forced to redo the whole nvidia installation (nothing seemed to be working right until I found a tutorial [here](http://albertomilone.com/latest_nvidia_udsf_edgy.html)).

Anyway, the point is that I FINALLY got my nvidia drivers working for the second time, but I realize sound died. I'm not sure when it occured, but it was sometime during the day when I was working with video card drivers (not even sure if its related, but its worth mentioning). Anyway, I've tried everything, but my sound card IS detected and my mixer settings are all pulled up and offmute. I opened hydrogen drum machine and played around with some drum sounds and every time I clicked a drum, the volume-light-bar thingies on the hydrogen internal mixer would show that sound was happening, but I couldnt hear it. I have no clue what is wrong and it is very annoying :( If someone could help me that would be great!

Once again, my sound card is detected, my mixer settings seem to be correct and certain apps respond as though sound is occuring, but I cant hear anything.

---

### Post by chriscando on 2006-11-05
> Once again, my sound card is detected, my mixer settings seem to be correct and certain apps respond as though sound is occuring, but I cant hear anything.

Maybe its your hearing. JK!! What program are you using to check your mixer settings? I have had luck using the terminal program alsamixer to up the volume and mute/unmute certain sound devices. Maybe give that a check.

Other than that is this a laptop or a desktop with speakers connected? If its the latter maybe check the physical connections or try something else like headphones to see if you can hear anything.

---

### Post by insertwackynamehere on 2006-11-05
i've looked at alsamixer and volume control (gnome). it is a desktop with speakers and then headphones through the speaker system. I have not changed its setup recently (though I check the sound cable to make sure it was plugged into the system) and I know the physical aspect of the speakers is fine because when I boot into XP, I get sound. Also, I was getting sound fine until some time today when I realized things were eerily quiet in Ubuntu ^_^ bleh I wanna figure this out though, its so annoying, I wanna play doom3 badly. I played it on windows before but now I can finally play it in all its glory since Linux seems to have no problem with me running it with almost everything way up (whereas windows would constantly freeze and crash on normal settings and have device failures like it does for any opengl application after a while)

---

### Post by Cable on 2006-11-05
Deleted.  Sorry, didn't read the first post as well as I should have.

---

### Post by insertwackynamehere on 2006-11-05
i should also add that when i unplug the sound cable that goes from my card to my speakers, i can hear crackling and stuff, and when i touch the line to metal i get interference which i can also hear, so the speakers and setup are fine

---

### Post by insertwackynamehere on 2006-11-05
Ok I have fixed this.

For reference to other users who may come across this problem:

I own Creative speakers (I-Trigue L3500) and they have a little volume control pod with headphone/mic jack and volume/subwoofer control. All I needed to do was turn off the volume on the little knob and then turn it back on..suddenly it worked. I'm not sure if it was some weird thing with the little volume control speaker device or if it was the way linux handles it (the latter is doubtful as I dont believe the two things every directly interact). So yeah it was just a weird speaker problem.

---

