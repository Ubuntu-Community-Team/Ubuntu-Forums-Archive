---
title: "Problem with streaming video/sound."
date: 2008-02-15
forum: General Help
---

### Post by hsinner on 2008-02-15
I seem to be getting video lag and no sound at all while playing videos on youtube. My sound card is a C-Media PCI CMI8738, video card is a ati x700 pro agp, and a MSI motherboard with a VT8237R Chipset. Rhythmbox music player also doesn't play music, all that plays is static.

---

### Post by danwood76 on 2008-02-15
It sounds like 2 seperate issues here.

1. Flash Plugin not installed correctly (non-free plugin is required for good video playback)

[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)
This thread has the correct version of the flash plugin and a guide to install it

2. alsa driver is possibly muted.

Open the terminal and type
```

alsamixer
```

Check all the volumes are high and un muted.

---

### Post by hsinner on 2008-02-15
I just installed Ubuntu a couple of days ago, so where exactly is the terminal?

---

### Post by danwood76 on 2008-02-15
The terminal is a command line interpreter.
In general you dont need to use it, but it is very useful when trying to solve hardware issues.

If you click applications in the top left, then accessories you will find it in there.
if you just type that command I posted earlier and press enter it should open up an audio mixer within the terminal window.
This will have all the volume controls and gives more control than the Gnome Volume Control.

---

### Post by hsinner on 2008-02-15
I checked the mixer it says- Card:VIA 8237, Chip:Realtek ALC655 rev 0, View:[playback] capture all, Item: Master [dB gain=0.00,0.00].

Master: 100<>100
Master M: 81
PCM:81<>81
Surround: 0<>0
Surround: shared
Center: 100
LFE: 0
Line: 74<>74

---

### Post by danwood76 on 2008-02-15
Select the surround option and turn it all the way up and see if you get sound.
It looks to be the only option muted.

---

### Post by hsinner on 2008-02-15
I already put my surround up, no luck. But for my Rhythm box player, it still continues to have a snowy/static-ish kind of a sound. Music DOES play just fine however on Totem Movie player (albeit low quality).

Still somewhat confused about the link you gave me. =\

---

### Post by ubuntu-freak on 2008-02-15
Follow my [how-to](http://ubuntuforums.org/showthread.php?t=661833) from the beginning and take a look at paragraph 7 in the troubleshooting section regarding your flash problem.
 
Nathan

---

### Post by hsinner on 2008-02-16
Don't really know if I'm doing something wrong or not...but it seems to do nothing. and in the essential packages I can't seem to get w32codecs to work.
Frustrating. =\

---

### Post by ubuntu-freak on 2008-02-16
Did you install alsa-oss? Did you enable the medibuntu repo? I marked it "IMPORTANT" so people wouldn't miss it. :-)
 
Nathan

---

### Post by hsinner on 2008-02-16
Things I have done so far: (successfully) installed the essential packages, installed flashplugin-nonfree, set FIREFOX_DSP=”none”" from none to aoss. Anything I'm missing?

---

### Post by ubuntu-freak on 2008-02-16
Flash vids still playing up? You could try the purge and install command I guess. Don't understand why you're having so much trouble. That aoss thing is the only real issue in FF for some users.
 
Nathan

---

### Post by hsinner on 2008-02-17
I used the "sudo apt-get purge flashplugin-nonfree && sudo apt-get install flashplugin-nonfree" command from your guide if that's what you mean.

EDIT: Sound can now play on flash vids but I still seem to be getting lag on videos, will enabling my graphics driver help?

EDIT (again): After enabling graphics, sound does not work again, I get a "The composite extension is not available" error.

---

