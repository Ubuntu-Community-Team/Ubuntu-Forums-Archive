---
title: "Amarok crashes when attempting to play mp3, fresh kubuntu 7.04 install"
date: 2007-05-29
forum: General Help
---

### Post by moljac024 on 2007-05-29
Ok, i've just installed kubuntu 7.04 because i wanted to give kde a shot....and by what i've seen so far things aren't looking very well for KDE...

It's filled with bugs, first it wasn't able to restart my computer it would just hang with a black screen, adept isn't nowhere near synaptic (the damn thing is buggy as hell) and amarok, well,  when i try to open an mp3 file in it, it just hangs up (a window saying mp3 support isn't installed pops up but without any text, just a blank window) and i can't to anything but terminate it....of course a search for mp3, mp3 amarok, mp3 support or anything similar returns nothing in adept ??! What gives ? I'm out of ideas here....

---

### Post by TheMono on 2007-05-29
Odd about the empty window for amarok

Try this command:

sudo apt-get install libxine1-extracodecs synaptic

I agree with you and despise adept, synaptic works fine in KDE though. Amarok is the greatest thing since sliced bread though.

As far as the restarting is concerned, are you using GDM or KDM?

---

### Post by moljac024 on 2007-05-29
Well, it's a fresh kubuntu install so KDM...

E: couldn't find package : libxine1-extracodecs

Bah, don't bother, i'm never touching KDE again.....in my 20 min experience with it, i've seen too many cases of applications launching for 10 or more seconds and then nothing happening,crashes (i've even had system settings crash once) and general instability... back to GNOME!

---

### Post by cferthorney on 2007-05-29
> **moljac024 said:**
> Well, it's a fresh kubuntu install so KDM...

E: couldn't find package : libxine1-extracodecs

Bah, don't bother, i'm never touching KDE again.....in my 20 min experience with it, i've seen too many cases of applications launching for 10 or more seconds and then nothing happening,crashes (i've even had system settings crash once) and general instability... back to GNOME!

Its a shame you feel that way.  Even if you don't decide to use KDE, I would seriously persevere to get Amarok working.  In my opinion it really is the best player out there at present.  Especially if you are not a fan of putting Mono on your machine for Banshee.

Synaptic couldn't find libxine1-extracodecs ?  Did a search off extracodecs reveal anything?

---

### Post by TheMono on 2007-05-29
Sorry! My mistake! Every other xine package is libxine1-whatever

But the extracodecs one is libxine-extracodecs.

You may also want libxine1-ffmpeg.

---

### Post by moljac024 on 2007-05-29
> **cferthorney said:**
> Its a shame you feel that way.  Even if you don't decide to use KDE, I would seriously persevere to get Amarok working.  In my opinion it really is the best player out there at present.  Especially if you are not a fan of putting Mono on your machine for Banshee.

Synaptic couldn't find libxine1-extracodecs ?  Did a search off extracodecs reveal anything?

It's a shame that i choose a faster and stable desktop ? It isn't.

---

### Post by TheMono on 2007-05-29
Rubbish. A twenty minute experience with KDE certainly doesn't life you out of the 'don't know what you're talking about' crowd sorry.

Feel free to use whatever works for you. But no need to knock KDE like that. It is better for what I want to do, and not for someone who doesn't want to spend more than twenty minutes getting their computer set up.

That's not a case of better or worse, just different.

---

