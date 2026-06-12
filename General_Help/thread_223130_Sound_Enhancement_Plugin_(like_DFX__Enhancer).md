---
title: "Sound Enhancement Plugin (like DFX / Enhancer)"
date: 2006-07-25
forum: General Help
---

### Post by unwoken on 2006-07-25
I thought this would be very easy to find, but i have spent a lot of time looking and come up with very little.

I am getting extremely average sound quality when listening to mp3's using any of my sound players (e.g. xmms/amarok)on ubuntu.  The issue is not the sound card or quality of mp3's. 

the best (and only thing) I have found so far is located here: [http://www.xmms.org/effect.php](http://www.xmms.org/effect.php) - they are not free, but I will pay if they are the best i can get.  I would prefer to use Amarok, but good sound is more important to me.

Has anyone here ever used these?  And are there any better alternatives?


Also, are there any music players available in Ubuntu (excluding using WINE) that have sound enhancement plugins (at all)?  I will try anything.

As I said, I am very surprised that there are not plenty of these things around (or are there?), but i would be very grateful if anybody can help out.

u.

---

### Post by unwoken on 2006-07-27
hmmm.....

:confused: 

should i assume from the fact that nobody has responded that there are **no** free (sound enhancement) plugins for linux music players at all????

that's really strange.

can anyone help at all??

u.

---

### Post by Johan! on 2006-07-27
The equalizer in XMMS is not good enough?

---

### Post by Johan! on 2006-07-27
Read this topic if you want to use Winamp equalizer presets
[http://www.ubuntuforums.org/showthread.php?t=133126](http://www.ubuntuforums.org/showthread.php?t=133126)

---

### Post by unwoken on 2006-07-27
thanks for the link, but unfortunately my sound quality is not great no matter what i do with the equalizer.

i have dapper on 2 computers - both connected to my stereo, but for whatever reason, the sound out of my laptop is poor (highly distorted).  The cables are good quality, and even though i don't think the sound card is the best going around, i get pretty good sound on M$ (dual boot).

to remove distortions i have to lower the pre-amp so far that adjusting the stereo volume to near a good level causes feedback type issues.

on my other OS (M$ - same computer) i have installed the 'enhancer' plugin on winamp and get brilliant sound.  i would love to get something even remotely similar on dapper - but haven't been able to at this stage.

it makes so much difference, that is why i am surprised to find such a lack on linux.

---

### Post by Onyros on 2006-07-27
Make sure you set the volumes to around 80% (Master and PCM), I've found it removes a whole lot of distortion from the output with decent speakers.

Also, is there any Convolver plugin for amaroK or even for XMMS? For any Linux music player? I hate having to use the equalizer, and I have great wav files for a convolver plugin (like I used in foobar2000 - and nope, foobar2000, which is my favourite player ever, is not an option, it's too buggy in WINE).

---

### Post by Johan! on 2006-07-27
Maybe there's some information in this topic?
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

### Post by mrazster on 2006-07-28
Have you tried to turnoff/mute all lines and mics and other settings you don't use in alsamixer .?? This helped me alot getting rid off distortion.
Also as was posted before, lower the PCM and Master setting to about 80-85%...helped a little to.

---

### Post by caserio on 2006-07-28
Hi,

For highest sound quality use jackd + xmms + jack-rack. Also install cmt, ladspa and caps plugins: there are hundreds available, for free !
 
As for MP3, consider using a lossless audio compression encoder like FLAC instead...

Audio culture:
 [http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation](http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation)
[http://linux-sound.org/](http://linux-sound.org/)

---

### Post by arkangel on 2006-07-28
well I dont know maybe it is my imagination but  i like xmms a lot, but for one reason  mplayer sounds better,  maybe it is the engine ?

---

### Post by unwoken on 2006-07-28
Thanks for the suggestions of changing the alsamixer settings.  that has helped get rid of the distortion issues i was having.

unfortunately it has highlighted another issue.  I am using a laptop, and when i have the power cord plugged in there is a very loud buzzing noise which is constant - in the background.  Reducing the Alsa settings (even by a little) makes this much more noticable.

If i remove the power cord, the buzzing sound completetly disappears.  It looks like this could be a major issue if i want to play music though the stereo at anything near a decent volume.  

This is really very strange to me.  Does anyone know what i can do to fix this problem - aside from rely on battery power?  Has anyone had this problem?


*part of the reason why i was looking for an enhancer is that by increasing the application volume (without distortion) at any given system volume - the balance between buzzing and music is clearly improved - see below.



> **caserio said:**
> Hi,

For highest sound quality use jackd + xmms + jack-rack. Also install cmt, ladspa and caps plugins: there are hundreds available, for free !
 
As for MP3, consider using a lossless audio compression encoder like FLAC instead...

Audio culture:
 [http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation](http://ubuntustudio.com/wiki/index.php/Dapper:Studio_Preparation)
[http://linux-sound.org/](http://linux-sound.org/)


ok. wow.  my god...  there certainly are hundreds of them.  i have absolutely no idea what most of them do, but thank you very much for your information.

can i ask, if any (or which) of these you might recommend that might be able to potentially help me enhance the volume without creating distortion, (see above)?  I will see what i can find, but help is appreciated.

cheers,
u.

EDIT: all other volumes at 0 in alsamixer does nothing for the buzzing - but that doesn't exist when the power is not on, so i am not sure if that means anything...

---

