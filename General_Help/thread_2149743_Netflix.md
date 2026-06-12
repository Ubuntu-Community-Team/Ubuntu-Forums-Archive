---
title: "Netflix"
date: 2013-05-29
forum: General Help
---

### Post by iamrandy on 2013-05-29
i found a website that showed me how to install netflix on ubuntu and it downloaded and installed everything but i couldn't get the netfliix desktop  to work. and it said something about i needed ms true type fonts and i couldn't find them either. I have the  ubuntu 13.04 if anyone could help me it would be greatly appreciated

---

### Post by LadyC 007 on 2013-05-29
Honestly, I tried this and there was ALOT of bugs and lagging.  I gave up and bought a blu-ray player with the netflix app. :) Goes well and was not expensive.  I know I don't answer your question but my experience was not good with netflix on linux. I also have ubuntu 13.04.

---

### Post by iamrandy on 2013-05-29
well thank you very much i kinda thought that when the website even said it had bugs. oh well thanks again

---

### Post by oldos2er on 2013-05-30
```
sudo apt-get update && sudo apt-get install ttf-mscorefonts-installer
``` When the EULA pops up use the space bar to page down, Tab to highlight "Ok" then Enter.

---

### Post by jawshoeaw on 2013-11-15
Didn't work, no fonts downloaded

---

### Post by efflandt on 2013-11-16
Have you installed "Ubuntu restricted extras" from Software Center (or ubuntu-restricted-extras using apt-get or synaptic)? That includes true type fonts (plus flash and various audio/video codecs), but also requires you to accept the EULA before the the fonts download.

Even in 12.04 Netflix desktop can be temperamental at times. I installed it awhile ago, but never used it because it always said I was missing a suitable gecko version (Internet Explorer substitute). But then one time when I followed the link in the popup to see what gecko I would need, Netflix suddenly came up and started working. It still comes up with that missing gecko popup, but if I cancel that it usually works. More recently it only seemed to load to a white screen, but after subsequent updates it is working again now.

Netflix is also quite broken if you output it from an Android phone to HDMI (videos that are wide screen on the phone are low quality horizontally squashed and pillar boxed when output to HDMI HDTV). So easiest and best quality to stream it is using a network connected BluRay player

I have mostly been using Hulu Plus for TV shows, which does not require jumping through hoops like Netflix does. Hulu also works fine output to HDMI from an Android phone, but is limited to 480p on a phone.

---

### Post by psfal on 2013-11-18
This is for Ubuntu 12.04 and up

If you've already installed the restricted-extras package, which includes ms truetype fonts:
```
sudo apt-get install ubuntu-restricted-extras
```

And installed all your multimedia stuff:
```
sudo apt-get install libavformat-extra-53 libavcodec-extra-53 libdvdread4
```
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

I'd suggest installing VLC also:
```
sudo apt-get install vlc
```

Just go here: [http://how-to.wikia.com/wiki/How_to_watch_Netflix_(Watch_Instantly)_in_Linux](http://how-to.wikia.com/wiki/How_to_watch_Netflix_(Watch_Instantly)_in_Linux) and do this,
```
[FONT=Verdana]sudo add-apt-repository ppa:ehoover/compholio[/FONT]
``````
sudo apt-get update && sudo apt-get install netflix-desktop
```

You should have no further problems with Netflix, I've done this several times with no issues... Although I think I might have installed wine 1.6 first, but probably not, if you want wine 1.6 do this:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa -y; sudo apt-get update && sudo apt-get install wine1.6 -y
```

---

### Post by mrag on 2013-11-18
I am somewhat embarrassed to admit to being only a part time Linux user who is not too bright to start with (with Windows or Linux). Over the last year(?) I''ve installed and tried several times to get Netflix to play on my 12.04 system. Tried being the active word as I never got anywhere. I wonder about following the instructions above-will they over write anything I might have done already? Are there items I should remove or delete first (and how)? Is here now (Nov 2013) a fool proof way to play Netflix on 12.04 (or other version)?

Basically, is there a primer for real dummies that have tried before, but still want to try Netflix once again on 12.04?

---

### Post by psfal on 2013-11-18
> **mrag said:**
> I am somewhat embarrassed to admit to being only a part time Linux user who is not too bright to start with (with Windows or Linux). Over the last year(?) I''ve installed and tried several times to get Netflix to play on my 12.04 system. Tried being the active word as I never got anywhere. I wonder about following the instructions above-will they over write anything I might have done already? Are there items I should remove or delete first (and how)? Is here now (Nov 2013) a fool proof way to play Netflix on 12.04 (or other version)?

Basically, is there a primer for real dummies that have tried before, but still want to try Netflix once again on 12.04?

Having no idea what you've already installed/tried to install, I couldn't tell you if this will safely overwrite whatever you've done. Truthfully when in doubt, reinstall the OS, it only takes about 20 minutes if you've backed up your data, only about 30 if you need to copy your entire home folder onto a USB first. Others might disagree but that's what I'd do personally. I will tell you that this Netflix Desktop install has always worked for me without hassle on my 12.04 machines...

I hope that helps :-)

---

