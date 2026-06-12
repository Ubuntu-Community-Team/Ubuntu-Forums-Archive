---
title: "[SOLVED] How to switch between audio devices?"
date: 2008-02-01
forum: General Help
---

### Post by kung fu buntu on 2008-02-01
I have an audigy 2 card as well as an onboard audio device.

alsamixer shows both of them in /proc/asound/card0 and card1. Although directory card1 as significantly less "items".

I would like to plug my speakers on card1 (on board audio device) in order to find out the source of some **terrible audio crackling sounds!**!! :mad: I need to know if its the card or the speakers.

So how can I tell Linux to use card1 instead of card0?

Thank you :guitar:

---

### Post by aeiah on 2008-02-01
set the default card to card1 using the asoundconf command. i think its something like asoundconf set-default-card card1

asoundconf --help should make things clearer

---

### Post by kung fu buntu on 2008-03-01
Nope. That didn't change anything.
I still get sound from Audigy2 (e.g. youtube videos), although amarok stoped working and I had to delete ~/asound* files.
My steps:
asoundconf list
asoundconf set-default-card Intel
alsa force-reload

I'm using Debian.

Any ideas for this?

---

### Post by kung fu buntu on 2008-03-02
I still haven't solved this, but I got a bit closer.
So what I have done:
```
		cat /proc/asound/modules
		nano /etc/modprobe.d/sound
			alias snd-card-0 snd-emu10k1
			options snd-emu10k1 index=0
			alias snd-card-1 snd-hda-intel
			options snd-hda-intel index=1

		asoundconf list
		asoundconf set-default-card Intel
			nano ~/.asoundrc.asoundconf
				defaults.pcm.card 1
				defaults.ctl.card 1
				defaults.pcm.device 1
				defaults.pcm.subdevice -1
		(as root... maybe not needed) alsa force-reload
		alsamixer

```

This solves the "xine was unable to initialize any audio drivers." error message given by amarok.

Sound is no longer redirected to *Audigy2* (because I no longer have sound neither in amarok nor vlc), if it goes to *Intel* I don't know... because ATM I don't have sound. And yes, I have plugged the speakers to the other card.

Any ideas?

---

### Post by arimaniac on 2008-03-03
Hi there

I wrote a complete HOWTO on disabling your on-board card

[http://ubuntuforums.org/showthread.php?t=712908]("http://ubuntuforums.org/showthread.php?t=712908")

Please reply with your
comments to improve the HOW TO...

Hope it helps....

---

### Post by kung fu buntu on 2008-03-04
I don't want to disable my on-board card.
I want to switch my active sound card, from Audigy2 (PCI) to Intel (on-board). And do it in a way that it isn't required to reboot the system.

I have been able to reditect the sound from Audigy2 to somewhere else, "else" which should be Intel audio... but it isn't and I don't know why.

---

### Post by kung fu buntu on 2008-03-09
Anyone?

---

### Post by Yellow Pasque on 2008-03-09
Well, I have no idea how to do it in ALSA, but maybe there's a way to do it through BIOS. I also know there's a way to "hide" PCI devices by using a boot parameter. I just saw a few threads on it; will let you know if I happen upon it again.

EDIT: Here's something about hiding PCI devices in Debian Etch [http://www.nabble.com/debian-etch,-how-to-hide-a-pci-card,-pv---hvm-xen-3.2.0-td15106023.html](http://www.nabble.com/debian-etch,-how-to-hide-a-pci-card,-pv---hvm-xen-3.2.0-td15106023.html)

---

### Post by erginemr on 2008-03-10
I don't know if it is what you are looking for, but there is a trick to put the available sound cards in order here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

under the section: "Configuring default soundcards / stopping multiple soundcards from switching".

This thread:
[http://ubuntuforums.org/showthread.php?t=114551](http://ubuntuforums.org/showthread.php?t=114551)

may also give a new aspect to the problem.

---

### Post by kung fu buntu on 2008-04-19
(for future reference... Also keep in mind that I use Debian, so the config files may differ a bit)

I have been busy but there was one day that I was so tired of hearing the crackling sound that I just had a go at it.
It is similar to the solutions that erginemr posted here, but you don't have to restart your system.

```
#nano /etc/modprobe.d/sound
alias snd-card-1 snd-emu10k1
options snd-emu10k1 index=1

alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0


#alsa reload
```

---

### Post by Yellow Pasque on 2008-04-19
Please use the thread tools and mark the thread SOLVED. Thanks.

---

