---
title: "TuxNes sound help!"
date: 2005-10-30
forum: General Help
---

### Post by mhancoc7 on 2005-10-30
I have been playing around with some of the various gaming emulators such as znes, stella, and tuxnes. I have got the sound working on them all except for tuxnes. The program runs flawlessly, except for sound. Does anyone have any tips for getting the sound to work in tuxnes?

Thanks in advance, Jereme

---

### Post by mhancoc7 on 2005-11-02
Just wanted to give this one bump.
Thanks, Jereme

---

### Post by mhancoc7 on 2005-11-02
Ok I got this one figured out. Here is what I did to get sound and my new gampad to work with tuxnes.

1.  Goto System->Preferences->Sound and disable "Enable Sound Server Startup"
2.  Install libesd-alsa0 which will remove libesd0, but that's ok.

Now sound works in all my emulators (tuxnes, znes, stella) as well as SuperTux!

I lost my system sounds, but that really does not matter to me.

I also got my gampad to work by selecting Enable Joystick 1 Device in GTuxNES. I then changed the line to /dev/input/js0. 

Now I can play my favorite childhood games from Atari, NES, and SNES!!!!

Jereme

---

