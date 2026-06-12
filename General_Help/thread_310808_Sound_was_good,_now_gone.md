---
title: "Sound was good, now gone"
date: 2006-12-01
forum: General Help
---

### Post by larryalk on 2006-12-01
I had to scrap the motherboard that had Kubuntu on it.  It gave perfect sound including system sounds, UTube! and playing music.

While setting up the new motherboard, I accidently booted the Kubunt and the KDE startup sound came up fine!

But when I removed the cd and booted up the old system hard disk, my sound was gone entirely.

How can I get back my formerly great sound?

Larryalk

---

### Post by bettlebrox on 2006-12-01
maybe one of the volume settings got set to zero? Try aumix or alsamixergui and have try changing the different volume setting.s

---

### Post by Johan! on 2006-12-01
Try these commands in a terminal, maybe it will help you:
```

sudo dpkg-reconfigure alsa-base

sudo dpkg-reconfigure alsa-utils

sudo /etc/init.d/alsa-utils reset

sudo /etc/init.d/alsa-utils restart

```

---

### Post by larryalk on 2006-12-01
Johan my mixer settings appear to be ok.

Beetlebrox:
I tried all three of your settings.
Now when I switch to another window I get a sound but nothing on utube which is how I test.

Any other ideas?

---

### Post by larryalk on 2006-12-01
When I said I get "a sound" I meant a kind of "uh" sound that just sounds a musical note and stops.

So _something_ is working but I'm getting nothing on utube.  Haven't tried playing an mp3 yet

Something is definatly wrong but I have proved that sound can be outputted.

Sound is so unnecesararily mysterious on Linux.  I like Linux but sound should be easy.

---

### Post by larryalk on 2006-12-01
Now there is something else really funny that has never happened before.

when I click on another of my KDE windows, I get a sound.  This never used to happen.

Actually I don't mind it so much as where is my normal sound?

Larryalk

---

### Post by bettlebrox on 2006-12-03
Sounds like something else is blocking access to the sound card. Do you have esd or arts running?

---

