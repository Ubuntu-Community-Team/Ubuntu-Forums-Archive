---
title: "Crackly, popping sound in games"
date: 2007-04-11
forum: General Help
---

### Post by kc0eks on 2007-04-11
ello all,

I have been working on this problem for a while now and havent found a good solution, this seems to be one of the larger problems coming from windows for me...The problem is that the sound is crackly and sounds terrible in any 3d games. Playing MP3's or video seems to work fine.

Onboard sound (Asus m2n32MB) which is a nVidia nForce 590 SLI chipset worked fine, but presents problems in any type of 3d games (Supertux and all others ive tried)to try and fix this I have installed the latest ALSA drivers, and tried a number of things I found on forums...nothing worked, but some made it worse..
Given that the onboard sound seems to suck even in windows I opted to try a different soundcard...

SO I got a soundblaster audigy SE. I just finished installing this with the latest ALSA drivers, and was quite disapointed upon loading a game and finding it does the exact same thing as the onboard sound (which is now disabled in the bios)
For the Audigy card I added this to my .asoundrc file per the ALSA doc for this card:

pcm.ca0106 {
type hw
card 0
}

ctl.ca0106 {
type hw
card 0
}
With or without the .asoundrc addition the sound is terrible in games. I have also tried setting the mixer volumes low, and muting what I dont need, this also had no effect.

I am at a loss of what to do next, please help me I want to play some of these very interesting linux games without the oh so annoying snap crackle and pop!

After some guidance at linuxquestions I tried OSS rather than alsa and it worked great soundwise (no popping, smooth sound) but it caused the OS to hang with simple tasks (running a game, closing konsole) the mouse would move but the os was unresponsive and only a hard reset fixed it. 

the following games present problems, there may be others but this is all ive tried:
Tuxracer and supertux
warzone 2100
astromenace

they do not present errors when run from a console

SO basically does anyone know how to fix ALSA to like my setup or make OSS work without crashing everything? 
thanks to all!

---

### Post by der_joachim on 2007-04-12
In the past, when I had such issues, I just set my PCM at 60-70%. Worked every time.

---

### Post by kc0eks on 2007-04-12
> **der_joachim said:**
> In the past, when I had such issues, I just set my PCM at 60-70%. Worked every time.

Unfortunately this fix has had no effect on the crackle, ive set every single channel to 50% or so and it still crackles like crazy. I have also muted all channels I dont use, including all inputs since I dont use a mic or anything. Playing with these various volumes just doesnt seem to help at all. And while using OSS I could crank everything to 100% and all sounded clear and smooth, except everything just kept crashing ;P

I appreciate the tip though. :)

---

### Post by Nikusan on 2007-05-07
Similar problem here. Totem/Rhythmbox are unaffected but nexuiz/wesnoth/planet penguin racer are.

Edit: this fixed it for me -- [http://ubuntuforums.org/showpost.php?p=2378018&postcount=3](http://ubuntuforums.org/showpost.php?p=2378018&postcount=3)

---

### Post by kc0eks on 2007-05-07
> **Nikusan said:**
> Similar problem here. Totem/Rhythmbox are unaffected but nexuiz/wesnoth/planet penguin racer are.

Edit: this fixed it for me -- [http://ubuntuforums.org/showpost.php?p=2378018&postcount=3](http://ubuntuforums.org/showpost.php?p=2378018&postcount=3)

well after 2 months of trying so many things to get this solved it seems like this has fixed it for most of my games (supertux is the only that sounds bad now).

I can hardly thank you enough for this!

---

### Post by daschmidty on 2007-06-19
Changing to oss instead of alsa worked for me.
```
sudo  apt-get install libsdl1.2debian-all alsa-oss
export SDL_AUDIODRIVER=dsp
```

---

### Post by exploder on 2007-07-04
I am so glad I did a forum search! This fix resolved my sound problems too!

---

