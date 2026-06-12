---
title: "trouble with dosbox and ethernet config utility"
date: 2005-07-17
forum: General Help
---

### Post by otakuj462 on 2005-07-17
Hi all, I'm trying to use dosbox as a DOS command prompt emulator to run a DOS configuration utility on my old 3c509 ISA Ethernet card.  Whenever I try to run dosbox, though, it gives me this error message:

Can't init SDL No available video device

I'm running Ubuntu on a very old PC (pentium 133, 64 megs of ram), and I haven't installed a Window System.
Does anyone know what the error here is? Do I need a Window System to run dosbox, or will it run straight from a command line interface? If I can't get dosbox to work, can anyone recommend another DOS emulator that they've gotten to work on Ubuntu?
Thanks.

-Jake

---

### Post by Wardhog on 2005-07-18
I think this means that the libSDL package (which dosbox requires) hasn't been installed.  I ran into a lot of these errors when trying to use dosbox, and once I got libSDLxxxxxxx installed, they all went away.

---

### Post by otakuj462 on 2005-07-23
Ok, so I did apt-get install on libsdl1.2debian-all
I now get the following series of error messages when I try to run doxbox:

Warning: Unable to initialize AAlib mouseUsing AAlib driver: Slang driver 1.0 (slang)
ALSA lib confmisc.c:550:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:387:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:945:(snd_func_refer) error evaluating name
ALSA lib conf.c:3463:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3932:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2068:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

Dosbox then opens, but all the graphics are all screwed up and it doesn't process input correctly. I cannot even return to the command line, and I have to restart.

Does anyone know what the error is here?

-Jake

---

