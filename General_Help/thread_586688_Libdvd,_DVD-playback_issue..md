---
title: "Libdvd, DVD-playback issue."
date: 2007-10-22
forum: General Help
---

### Post by lodravah on 2007-10-22
Heyall..

I just installed Gutsy, and I'm having some issues with DVD-playback. I can play some DVD's fine using Totem and VLC (have not installed Gxine-package), but some DVD's won't play. Errormsg reads in totem that the correct codecs aren't installed. So I was thinking of reinstalling libdvd, but can I use the one from feisty, since I can't find the one for Gutsy? 

Also, a question about repo's for Gutsy. Does it work like it alwasys has. Usually i got repos from ubuntuguide.org - wikis, and they worked fine. But now I can't find any for Gutsy..

hvard

---

### Post by UK-Wobbie on 2007-10-22
> **lodravah said:**
> Heyall..

I just installed Gutsy, and I'm having some issues with DVD-playback. I can play some DVD's fine using Totem and VLC (have not installed Gxine-package), but some DVD's won't play. Errormsg reads in totem that the correct codecs aren't installed. So I was thinking of reinstalling libdvd, but can I use the one from feisty, since I can't find the one for Gutsy? 

Also, a question about repo's for Gutsy. Does it work like it alwasys has. Usually i got repos from ubuntuguide.org - wikis, and they worked fine. But now I can't find any for Gutsy..

hvard

You have not got all the pluggings to play some DVDs..  Open Terminal!

This code is for mp3 and music files and stuff.


```
sudo apt-get install ubuntu-restricted-extras 
```


Then for dvd playback and even more codecs

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs] 
```


All codes are for date plugings like DVD,Music,Images...
Like codes for PNG,JPG And so on. :)

---

### Post by lodravah on 2007-10-22
All right, thanks. 

I have installed all the gstreamer-packages with codecs from add/remove, so mp3/avi and such does work nicely. But I guess it won't matter if I install them again, just to make sure.

But the repo's for Gutsy are still something of a mystery to me. Like installing Skype for instance (dl'ed the .deb from their site, so it works now, that's not the issue). I couldn't find Skype in any of the repo's used by synaptic or add/remove. Where can I find updated repo's for Gutsy when that time comes? Or is it new that they are automatically updated? Like with Edgy and Feisty I used repos from ubuntuguide.org/wiki, very easy peasy. Are they going to do the same thing with Gutsy?

hvard

---

### Post by bluedragon436 on 2007-10-23
I had to mess around with the updates a few times, but got it all working now...Much Thanks to you guys for your assistance!!!

---

