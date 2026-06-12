---
title: "sound issue."
date: 2008-05-17
forum: General Help
---

### Post by chinchilla2392 on 2008-05-17
my sound has been completely fine up until about 2 hours ago.
i havent made any installs which could have encouraged this. 'thing'
heres the problem
it seems to be that the 'PC Speaker' on alsa is picking up interference or god knows what
it starts with the initial little drum when i log on 
and if not muted can be ear-splitting.
ive tried reinstall alsa, alsa-base etc. is there any fixes for this? anyone else encountered this problem?
im using 8.04 if thats helpful

---

### Post by joshsmith on 2008-05-17
go into the gnome-volume-control, enable all the track  in edit>preferences, and mute everything you dont want to hear (ie basically all the tracks)

repeat if you have several devices

---

### Post by chinchilla2392 on 2008-05-17
i dont want it muted. lol
i want it to work!
cuz right now if i have the PC Speaker slider unmuted
its ear-splitting and is picking up interference. and if i mute it
no web browsers get sounds on youtube and sites like that

---

### Post by Gunman1982 on 2008-05-17
you can check if another program tries to interfere with the sound ouput, open a console and execute 'lsof | grep snd' and look which programs access the soundcard (first column)

---

### Post by joshsmith on 2008-05-17
i wasnt saying mute everything, but basically everything. 

a lot of other tracks can output static, so go and mute them, whilst leaving your main (usually called pcm)  track unmuted

---

### Post by chinchilla2392 on 2008-05-17
i fixed it with some stuff. lol
thnx anyways

---

### Post by joshsmith on 2008-05-17
so post the fix so that other people can read it

---

### Post by Johnson on 2008-05-17
How did you fix it? Because I have same problem!

---

### Post by chinchilla2392 on 2008-05-17
ok well. 

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

then

sudo apt-get install linux-sound-base alsa-base alsa-utils

and if you see it removed gdm

sudo apt-get install gdm ubuntu-desktop

then reboot
if you had a themed gdm
it will be set to default
but it resets alsa and the sound configuration
tell me if it works

---

