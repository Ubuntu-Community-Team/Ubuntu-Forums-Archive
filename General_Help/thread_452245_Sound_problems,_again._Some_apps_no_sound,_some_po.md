---
title: "Sound problems, again. Some apps no sound, some poor sound, some work fine"
date: 2007-05-23
forum: General Help
---

### Post by kc0eks on 2007-05-23
Hello all,

My ongoing problem with sound still seems to be hanging around. I have always had sound, but it was poor, or didnt work in all apps. this still continues.

I am using a Soundblaster audigy SE card, after giving up on my xfi and onboard sound. 
Running Feisty Kubuntu. Using the ALSA sound system according to KDE control.

in an attempt to solve the crackly sound issues I was having someone posted that doing this would help, and it did:
Installing libsdl1.2debian-oss instead of libsdl1.2debian-all

I also found somewhere online to run the app with "aoss appname" so I tried that as well, sometimes it helped sometimes it didnt.
however now I seem to have a few games that wont play sound at all. Those that do play sound for the most part sound ok. I have no idea what to do so I have documented what several games do:

*chromium - sound works- crackles

*Zsnes - regular-no sound (with aoss bad sound)

*lbreakout2- no sound - aoss doesnt make a difference
No available audio device
Couldn't open /usr/share/games/lbreakout2/gui_theme/click.wav (Audio device hasn't been opened)

*abe - Mix_OpenAudio: No available audio device -and game wont load
With aoss game loads and sounds seem fine

*supertux - sound crackle

*ActionCube- sound init failed (SDL_mixer): No available audio device
with "aoss actioncube" sounds fine


I have searched around trying to fix this but havent gotten far, any idea? I greatly appreciate it!

---

### Post by Necreia on 2007-05-28
I haven't ran into 'no sound' issues, however I have an Audigy SE and get the crackles.

If I figure anything out I'll let you know... driving me nuts too.

---

### Post by kc0eks on 2007-05-28
> **Necreia said:**
> I haven't ran into 'no sound' issues, however I have an Audigy SE and get the crackles.

If I figure anything out I'll let you know... driving me nuts too.

all these sound problems I am having dont seem to be very common, so I am beginning to wonder if its an incompatibility somewhere, motherboard perhaps, who knows.

Im not sure which is more annoying, no sound, or really crackly sound... :P

---

### Post by commandergc on 2007-06-25
The crackling sound is a known issue with many soundblaster cards :( 
One possible fix for this is to go into your motherboard's BIOS and set the PCI latency to 32ms.  Setting the latency to 32ms has fixed this problem for me, except for the new SB xfi series cards ( i had to change the motherboard to fix it).

---

### Post by kc0eks on 2007-06-25
> **commandergc said:**
> The crackling sound is a known issue with many soundblaster cards :( 
One possible fix for this is to go into your motherboard's BIOS and set the PCI latency to 32ms.  Setting the latency to 32ms has fixed this problem for me, except for the new SB xfi series cards ( i had to change the motherboard to fix it).

I have not heard of trying that one yet, so I shall do so next time I reboot. Appreciate the info :)

---

### Post by kc0eks on 2007-06-26
> **commandergc said:**
> The crackling sound is a known issue with many soundblaster cards :( 
One possible fix for this is to go into your motherboard's BIOS and set the PCI latency to 32ms.  Setting the latency to 32ms has fixed this problem for me, except for the new SB xfi series cards ( i had to change the motherboard to fix it).

Ok so I have seen that option before, but I suppose not on this MB. I looked through all of the settings and the book but found nothing that looked like this option. It is an Asus m2n32 board and has options for more things than any board I have ever had, so it seems like this one would be there...perhaps it is called something else.

If anyone knows please let me know, otherwise the google hunt begins!

---

