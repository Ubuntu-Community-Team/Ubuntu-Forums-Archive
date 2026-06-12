---
title: "Inconsistent USB Audio in Kubuntu 7.10"
date: 2007-12-11
forum: General Help
---

### Post by mojavejoe on 2007-12-11
Okay, let me preface this by saying I think i thoroughly researched this and I haven't really seen anybody reporting the same symptoms I'm having....Also I'm really new to this whole linux thing.  Installed at the end of November.

Basically what happens is that everytime I turn on my computer and load up Kubuntu, it's a gamble as to whether or not I will have audio.  Usually on the third or fourth try I get it.  I use an admittedly cheap USB audio device (shows up as "C-Media" in lsusb) which I only bought because the speaker jack on my SoundBlaster LIve card got messed up and affected the sound quality.  

On the days that it works I can run asoundconf -list and see that I have 2 sound cards.  I've long ago set the USB to defualt so it always shows up as the default when it decides to show up.  

On the days that it does not work, it doesn't even bother showing up in asoundconf -list.  Just the SoundBlaster shows up.  

One of the whole reasons I have this computer is for music and if I don't get sound it's utterly pointless and I'll just have to run back to Windows with my tail betwixt my legs.  

Another note I should mention is that I chickened out having tried unsuccessfully to install another build of linux in the past.  I dual booted, so I still have XP on another internal hard drive.  I also noticed another trend that I think is associated with the dual boot.  That being that if I run Windows, shut down the computer, then go to turn it on and boot Kubuntu, it refuses to recognize my ethernet port... the only way I can get my ethernet back is by logging back onto windows then doing a warm restart and going to Kubuntu.  Needless to say I can seldom ever get a load where I have both internet and sound.  God forbid.  

Sorry for the long story, but I am looking for help as to what I can do to get the USB audio device to regularly show up as a sound card.  One thing I should also say is that always is recognized by Kubuntu when i go into the Kinfo thing or type lsusb... it's just not getting over to the sound card list.  

Thanks for any help.

---

### Post by mojavejoe on 2007-12-15
More info on this... after doing more research over the past few days, I noticed that when I run dmesg it shows this error:

[ 1480.826531] snd-usb-audio: probe of 3-1:1.0 failed with error -5

I'm guessing this has something to do with why I'm not receiving USB audio... anyone know what I can do to remedy this error???

---

