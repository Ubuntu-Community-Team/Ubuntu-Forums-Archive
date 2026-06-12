---
title: "aoss feisty problem -  HeLp?"
date: 2007-04-20
forum: General Help
---

### Post by Ripfox on 2007-04-20
Ok so I was FINALLY able to start recording normally again with Audacity under Edgy using "aoss audacity" command. This was using alsa driver 1.0.13, but since I updated to Feisty, it installed a different alsa driver, which did see my on board mics but aoss audacity is very buggy now. It crashes and freezes and just doesn't work right. SO...I tried to recompile the old alsa driver, but I get this error on "make":  

make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/joneser/alsa-driver-1.0.13rc3  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/joneser/alsa-driver-1.0.13rc3/acore/memalloc.o
In file included from /home/joneser/alsa-driver-1.0.13rc3/acore/memalloc.c:1:
/home/joneser/alsa-driver-1.0.13rc3/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /home/joneser/alsa-driver-1.0.13rc3/acore/memalloc.inc:13,
                 from /home/joneser/alsa-driver-1.0.13rc3/acore/memalloc.c:1:
/home/joneser/alsa-driver-1.0.13rc3/include/adriver.h:742: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/home/joneser/alsa-driver-1.0.13rc3/include/adriver.h:761: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /home/joneser/alsa-driver-1.0.13rc3/acore/memalloc.inc:13,
                 from /home/joneser/alsa-driver-1.0.13rc3/acore/memalloc.c:1:
/home/joneser/alsa-driver-1.0.13rc3/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/home/joneser/alsa-driver-1.0.13rc3/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/home/joneser/alsa-driver-1.0.13rc3/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/home/joneser/alsa-driver-1.0.13rc3/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/home/joneser/alsa-driver-1.0.13rc3/acore/memalloc.o] Error 1
make[2]: *** [/home/joneser/alsa-driver-1.0.13rc3/acore] Error 2
make[1]: *** [_module_/home/joneser/alsa-driver-1.0.13rc3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2


So is it that i cannot use the old driver? 

This may be a Feisty deal-breaker for now....:(

---

### Post by vrix on 2007-05-05
using edgy, I had a high pitch noise when recording in audacity that's why I used aoss audacity command. then when I upgraded to feisty, using aoss adacity crashes when playing in audacity. what worked for me is running the audacity command (with no aoss), and changing the project sample rate to 48000, and it worked with no high pitched noise. I hope this helps.

---

### Post by Ripfox on 2007-06-02
yep...playback is now very unreliable, with aoss audacity. Still get the high pitched sound with no aoss, even changing it to 48000. Only solution I have is to back everything up immediately, and playback stuff through a third party application....anyone have any ideas??

---

### Post by ArtInvent on 2007-06-14
I have been having nothing but problems with Audacity since moving to Feisty. I got my mic working for a while, now it gives nothing but a full waveform of noise. I did all the Volume Control checking and unchecking of boxes, switched to using the also-oss wrapper and 'aoss audacity' command, trying various combinations of sound sources in all the usual locations. Audacity will load and play other files, although playback is spotty with random dropouts. Very aggravating.

Sound Recorder actually works (although it's buggy and doesn't seem to record anything until you try and shut down without saving and then save to ogg - resulting file sounds fine.) I can even record audio through LiVES video editing software. Mic sounds fine using recordMyDesktop. Just not Audacity.

Here's the ultimate rub: I have WinXP running in a virtual machine under VMWare Player on this Feisty host. I loaded the beta Audacity 1.3.2 on that and guess what? Flawless, even records at 96kHz. Same mic, etc. What on earth gives?

My specs: AMD X2, ASUS  M2NPV-VM mobo, ADI AD1986A onboard sound.

---

### Post by Ripfox on 2007-06-16
Agreed...we need a resolution to this problem. I am a musician who loves to create, unfortunately I don't posess the skills to rewrite a program ;)

Jokosher is FAR from working in my exp. 

P.S. don't tempt me to load xp into a virtual machine :o

---

### Post by ArtInvent on 2007-06-18
I love Audacity because it's exactly what I need, simple powerful audio waveform editor, hold the fat. Actually the 1.3 series is nigh on to perfect and has pretty much everything that 1.2.x lacks. If only 1.3 were available in repos and used ALSA (not sure what it uses, I've only loaded it on Windows.)

However, it might be possible in the meantime to go with a more elaborate program like Ardour. I see that Ardour 2 is now available in repos (not sure which repo because I have a lot of 3rd party.) It uses ALSA so that should resolve the OSS driver problems with Audacity. I've tried programs like this such as Cakewalk, Soundforge, Sonar, etc. but the multi-track trickery and all the in-out bus routing options are just a big unnecessary source of clutter to me, hence my use of Audacity. However, if you need a working Linux audio recorder, it would be worth a try. Ardour seems as capable a DAW as anything I've seen.

Ardour2 installed but there's no program launcher created. You have to start Jack first if it's not running already (I used the JACK control GUI) and then the CLI command ardour2. It seems to record a mic signal. But I now have a strange static clicking noise on all mic recordings. Kind of like clipping, but all the time. Sigh. You may have better luck.

---

### Post by ArtInvent on 2007-06-18
SUMMARY:  I now have a fully functional Audacity 1.2.6 in Feisty by installing alsa-oss, selecting the OSS devices in Audacity, and selecting any recording format OTHER that 24 bit samples. Works up to 96kHz with 32 bit float samples. Recording, playback, filesaving, import, export MP3 etc. all seem stable.

In Audacity I selected the OSS devices for I/O, and selecting any recording format OTHER that 24 bit samples.

EXPLANATION:  So after trying Ardour2 and getting the clicking problem, I decide to reboot. Still have the clicking problem. So just for the heck of it, I start Audacity 1.2.6 (non-aoss) and my mic-pinning-the-meter problem is gone. I have a clean signal from the mic. But no playback. I check the Prefs and get playback going by checking Audio I/O, Playback Device: ALSA: HDA NVidia: AD198x Analog (hw:0,0) and for Recording Device, the same. (This is my on-board 'High Definition' sound device.)

Then I double check by starting aoss audacity. Seems the same, everything is fine. Loads and plays mp3s. Saves well. Playback is solid with none of the stuttering. (Though playback can be made to stutter by resizing the window, using other program windows, but that seems like a minor issue and something I have noticed on other platforms.) by Cross your fingers, hold your breath, I think it's working . . . at least until the next reboot?

I also notice that I can get the mic to pin the meter again by trying to set the project to 24 bit sample. Switch back to 16 bit or 32 bit float and it's fine. Maybe this was the source of my problems. I would prefer to record in 24 bit because that's what all my hardware uses, and it takes less disk space than 32 bit. I also cannot record in 96 kHz or 88.2kHz, get an error saying 'cannot open sound device.' My card can record in 96-24 fine in Windows. 

SO NOW I go back and switch to the OSS devices for both recording and playback. NOW 96kHz recording works. It appears that the ALSA driver or aoss just doesn't work higher than 48kHz. It does not seem to make any difference whether starting 'audacity' or 'aoss audacity', both seem to work.

I still have two problems. One is that Audacity 1.3 is much better but can only be had building from source. Then, it doesn't seem possible to use VST plugin effects, this seems to be only available on Windows or Mac. I really like the Andwida Soft DX Reverb Light, it seems to be the class of free-beer reverbs. By doing a search in Synaptic for LADSPA and installing a number of plugin-looking things, I restarted Audacity and found a lot more plugins accessible. Freeverb and GVerb seem to be two possible replacements for Anwida. I always liked Anwida because the reverb sounds the best and easy to tune, and it's hard to get a bad sounding reverb out of it.

---

### Post by Ripfox on 2007-06-18
Thanks alot for the info...seems my problems were the same.

---

### Post by jadonchristensen on 2007-09-26
> **vrix said:**
> using edgy, I had a high pitch noise when recording in audacity that's why I used aoss audacity command. then when I upgraded to feisty, using aoss adacity crashes when playing in audacity. what worked for me is running the audacity command (with no aoss), and changing the project sample rate to 48000, and it worked with no high pitched noise. I hope this helps.


You are a genius man. I have been searching for hours trying to stop that squeal. I tried everything that I could find... changed it to the 48000, no squeal! Thank you! :)

It's in the bottom left corner of Audacity, if anyone is wondering where to change that to 48000 Hz.

---

