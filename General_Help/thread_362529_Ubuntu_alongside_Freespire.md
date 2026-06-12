---
title: "Ubuntu alongside Freespire"
date: 2007-02-15
forum: General Help
---

### Post by Danyl on 2007-02-15
Hi all

As usual, I'm hoping the Ubuntu forums can come to my rescue!

I've installed Freespire Linux to run alongside my Ubuntu (Edgy) distro mainly for my partner and other family members to use Linux (I chose Freespire for its similar appearance to Windows).

However, I have a problem with Flash 9 in Freespire that I have NEVER had with Ubuntu.

I managed to successfully download and install Flash 9 in Firefox in Freespire, however there is no sound when I visit Flash sites. The video plays fine.

I don't know if the issue might have something to do with KDE and Flash 9? Any Kubuntu users have this same problem?

I've tried EVERYWHERE to find a solution to this problem (the Freespire forums do not compare to the helpfulness of the Ubuntu ones). 

I've seen post concerning thing like ALSA instead of OSS etc etc (which I found a little confusing) but nonetheless have tried changing my settings in KDE accordingly, but nothing seems to be work.

I know this problem isn't exactly a Ubuntu issue (Ubuntu, you rock) but I'm hoping someone with more experience than me on this forum can lend a hand.

Freespire?! Arrrg!

---

### Post by tronica on 2007-02-15
well on the ubuntuguide.org site they have a solution for this problem, but i don't know if it will work.  So use at your own risk

> Note: if sound doesn't work in Flash Player (for example on YouTube):

sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

To:

FIREFOX_DSP="aoss"

    * Restart Mozilla Firefox. Now sound should work in Flash Player. 

---

### Post by Danyl on 2007-02-15
Thanks for the reply, but it didn't work. I got the following error:

"Failed to run gedit '/etc/firefox/firefoxrc' as user root:
 Child terminated with 1 status"

---

### Post by wh0rd on 2007-02-15
install alsa-oss:
```
sudo apt-get install alsa-oss
```

then run firefox with aoss prefix:
```
aoss firefox
```

---

### Post by Danyl on 2007-02-15
> **wh0rd said:**
> install alsa-oss:
```
sudo apt-get install alsa-oss
```

then run firefox with aoss prefix:
```
aoss firefox
```

Done. Still no sound. :( 

I get the following errors in the terminal:

```
nsKDERegistry::Startup
QApplication: There should be max one application object
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
```

Any thoughts?

---

### Post by Fibonacci on 2007-02-16
I don't think you need aoss with Flash 9 - it already comes with alsa support.

Do any other apps produce sound? What happens if you play some file with MPlayer?

---

### Post by Danyl on 2007-02-16
Yes other apps play sound fine. Ie Lsongs play Mp3's fine, Quicktime trailers play sound fine. It just appears to be Flash.

---

### Post by deanlinkous on 2007-02-17
sound problems on *spire - who would of imagined! :D

which version - release or beta?

Check to make sure alsa is completely installed - start there.

---

### Post by Danyl on 2007-02-18
> **deanlinkous said:**
> sound problems on *spire - who would of imagined! :D

which version - release or beta?

Check to make sure alsa is completely installed - start there.

Really? Is there a history of the *spire products acting up when it comes to sound? Just my luck (I'm a musician! I need my sound!) :) 

Its version 1.0.13 which I believe is the release version? (I could be wrong).

Alsa appears to be fully installed (I used Synaptic). I've even gone to the extent of installing all the modules (anything that had Alsa drivers in its description, I've installed!)

---

### Post by deanlinkous on 2007-02-18
search the forums for **jack** and **jackd**
This is one of the things the new version is suppose to correct - lets hope they get it right! Oh and if you try to remove jackd it will rip out most of the system as well. So dont try it! :D

---

### Post by Danyl on 2007-02-18
The solution has been found my friends!

It turns out I needed to create the following script:

> /bin/bash audiowrapper --alsa -- /usr/bin/firefox

and when I run this script, voila! Firefox sound is returned.

I created a Desktop shortcut to act as my execute file/app launcher so a double click, the script executes and we're back in business.

Thankyou so much everyone for your input. As usual, the Linux community has saved me yet again.

---

