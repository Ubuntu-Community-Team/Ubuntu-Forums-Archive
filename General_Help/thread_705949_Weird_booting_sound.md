---
title: "Weird booting sound"
date: 2008-02-23
forum: General Help
---

### Post by bradybunch226 on 2008-02-23
My sound wasn't working for a while then all of a sudden it started to work
(i was in windows at the time)when i tried to boot into ubuntu a lound high pitched sound came from my speakers while ubuntu started. I immeadatly took out my battery to stop the noise. Any idea what the problem could be??

---

### Post by Crafty Kisses on 2008-02-24
> **bradybunch226 said:**
> My sound wasn't working for a while then all of a sudden it started to work
(i was in windows at the time)when i tried to boot into ubuntu a lound high pitched sound came from my speakers while ubuntu started. I immeadatly took out my battery to stop the noise. Any idea what the problem could be??

That sounds really odd. Have you ever heard this noise before?

---

### Post by kaginken on 2008-02-24
That's really weird.  Is your laptop pretty old?  Got external speakers plugged into your sound card, or anything else like a microphone?  Spill any liquids into it lately?  lol

If it stopped when you removed the battery - was it still plugged in (AC Adapter)?  If so, is your battery on the fritz or getting old?  :confused:

---

### Post by Crafty Kisses on 2008-02-24
> **kaginken said:**
> That's really weird.  Is your laptop pretty old?  Got external speakers plugged into your sound card, or anything else like a microphone?  Spill any liquids into it lately?  lol

If it stopped when you removed the battery - was it still plugged in (AC Adapter)?  If so, is your battery on the fritz or getting old?  :confused:
That's what I was thinking, it could possibly be your sound card.

---

### Post by bradybunch226 on 2008-02-24
My laptop is bearly a year old and i had no externle speakers plugged in. Also It wasn't plugged into the ac adapter at the time i pulled the battery out and my heaphones were plugged in.

---

### Post by Toadmund on 2008-02-24
What brand of laptop is it?

---

### Post by bradybunch226 on 2008-02-24
It is a toshiba. I muted all sounds in windows and then booted into ubuntu and it didn't make that sound but i have no other sounds in ubuntu either. I'm going to boot into windows now to see if i still have sound there

---

### Post by bradybunch226 on 2008-02-24
I still have sound in windows. I saw another thread that said if you mute sounds in windows then boot into ubuntu you won't have sound in ubuntu so im going to un mute sounds in windows and try ubuntu again

---

### Post by kaginken on 2008-02-24
While you're troubleshooting this, eliminate any extra variables by NOT having headphones plugged in, or any other devices plugged into your soundcard.  This will help isolate the problem - if it is indeed your sound card.

Something else you can do in Ubuntu is to turn off that annoying internal 'BEEP' sound.  It's easy to turn back on if you need to, but in the meantime, you won't have to hear that sound and it may help

```
rmmod pcspkr
```

If you decide you miss it, this will re-load it:

```
    modprobe pcspkr


```

---

### Post by bradybunch226 on 2008-02-24
I re-installed my sound card driver in windows and now sound works in windows and ubuntu with no problems. Also i haven't heard that beeb again. Thanks for all your guys help

---

