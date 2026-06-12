---
title: "2 sound cards, alsa, sound, gnome, ubuntu, problems."
date: 2006-10-22
forum: General Help
---

### Post by Kallewoof on 2006-10-22
Hi!

I've got 2 sound cards, and I have three problems:

1. In Gnome's Sound settings, I try to change the default sound card and this fails. I do not have ESD running, and if I do gnome-sound-properties from a console, I see it tries to kill ESD (but no such process), which leads me to suspect that the sound properties are exclusively for ESD, BUT...

2. The volume control is "sometimes" using the right card and "sometimes" using the wrong card. So it's a hit/miss deal when I try to use it. If I'm lucky, it works. Yay!!!! If I'm unlucky it doesn't. Booo... This stems from the following problem: The order in which Alsa detects the sound cards is... random. Spectacularly enough.

3. Skype. Due to reason #2, I need to continuously go in and change the Audio In, Out, and Ringing devices as they are based on the numerical sound card slots, rather than the sound card names.

I've done the whole asoundconf set-default-card deal, and I've tried various other tricks too. If anyone has a way to make alsa detect the cards in the right order, that would most likely solve at least #2-3 for me. #1 is mostly an annoyance, because it's been around FOREVER and not been fixed. 

(And before you ask, I do not want to disable one sound card. I bought the other one because I wanted 2. :)

-Kalle.

---

### Post by miggl on 2006-11-21
I am having the EXACT same problem. Have you found a work-around for this?

---

### Post by Kallewoof on 2006-11-21
None. :(

-Kalle.

---

### Post by currentshades on 2006-11-22
Same problem here.

---

### Post by joegiampaoli on 2006-11-23
This guide might help you, i saved me setting up to audio devices on my Edgy.

Cheers ;)

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

### Post by currentshades on 2006-11-24
I take back my earlier post; keep trying with Ubuntu (SUSE still had problems with my sound)!  ;)  

I don't remember from where I got the solution, but it actually fixed my problem!!  OK, I'm trying to find it again; it was a blacklist.  I found this thread, which may hopefully help you.
[http://ubuntuforums.org/showthread.php?p=67707](http://ubuntuforums.org/showthread.php?p=67707)

But, that isn't the one that I used to fix my problem...OK...found it!
[http://www.linuxquestions.org/questions/showthread.php?t=493303](http://www.linuxquestions.org/questions/showthread.php?t=493303)

Basically, do this.
Open Terminal or Konsole and type the following.

```
sudo nano /etc/modprobe.d/blacklist
```

I added this to the end to disable the dang OnBoard sound.

```
# should be disabled according to BIOS
blacklist snd_via82xx
```

Now, if you do not know the name of the card/chip you want to disable, enter the following into Terminal or Konsole first and replace "snd_via82xx" above.

```
cat /proc/asound/modules
```

I hope this helps you!!  ^_^

---

### Post by miggl on 2006-11-27
Thanks for the replies!

One question though: will the onboard sound now be totally disabled, or will I still be able to pick and choose which applications use which sound device?

I want my sound card to be used with chat programs like TeamSpeak (etc.) and the onboard should be Ubuntu's default card for everything else.

Cheers, mates.

I'll report back in when I have fiddled around with it some more.

---

### Post by gavinmc on 2006-12-03
Hi,

A better solution is probably to change the index of the alsa sound cards.  I have two sound cards, which I can list as follows:

gavin@shuttle:~ $ cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with ALC650E at 0xec181000, irq 209
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7134[0] at 0xec002000 irq 201

The above is my tv card and on-board intel sound.  I cannot set the default gnome sound card either but found that the default gnome sound card is whatever sound card is "0", ie the first in the above list.

In most of the alsa sound driver modules you can give an "index=X" option when loading.  The saa7134 card was first in the list, but I wanted snd_intel8x0 to be 0.  So I opened /etc/modutils/options and added these two lines:

options saa7134_alsa index=1 
options snd_intel8x0 index=0

so now. when the modules load, they appear in the order above and the default gnome sound card is the intel one.

Gavin

---

### Post by gavinmc on 2006-12-03
It turns out this solution is in the "Comprehensive Sound Problem Solutions Guide"

[http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem](http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem)

under "Configuring default soundcards"

Gavin

---

### Post by Kallewoof on 2006-12-04
Gavin, thanks very very very much for providing the solution. I did read the comprehensive guide (I thought), but must have missed that part. :/ Thanks again, though. Things seem to be working awesomely now. :)

-Kalle.

---

