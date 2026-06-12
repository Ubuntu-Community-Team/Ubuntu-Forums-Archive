---
title: "Clicking Audio - Have Read Other Posts"
date: 2005-10-24
forum: General Help
---

### Post by some_random_newbie on 2005-10-24
keywords for searchers: audio static, clicking sound, static sound

Greets,

Most of my problems have been fixed thanks to searches on the forum, but after several days and exhausting search terms that I can think of I haven't been able to fix my audio.

Hardware:  Audigy 2 NX USB
Running: Ubuntu Breezy

Like many here I am a total newb to Linux, though, for however much it helps, I'm not a newb to PCs.

Problem:

The moment that I load into the desktop (xfce or default Ubuntu) I begin hearing clicking / static from the speakers once ever one second.  This has occurred since I was able to enable sound, so pretty much from day one.

This clicking plays regardless of other audio that may be playing, however, I can mute the clicking by muting system audio.  Also, I can adjust its audio by adjusting the sliders for the system volume.

PCM2:

This is forced to max volume or nothing.  Regardless of the mixer that I use and/or regardless of the audio player that I use and its settings, the PCM2 volume is forced to max volume.  I can mute it and, as it stands, I can slide it down to the bottom.  However, I wasn't always able to slide it to the bottom.  This is because the volume slider fights my mouse.  It does this now, although once it hits the bottom it stays.

If I mute PCM-2 audio then all sound in the system is muted.  Though I can adjust audio based on other sliders, muting PCM-2 mutes all sound regardless of other sliders' settings.

ALSA:

Not only does the clicking start as soon as I load into the desktop, but it continues until the system is rebooting and the text is scrolling by.  The clicking only stops once the "Stopping ALSA" (or whatever the exact quote is) text appears on screen while the system is shutting down.

Any feedback to get this fixed would be so very welcomed at this point...

Thank you,
~a lil newbie

---

### Post by mikedtemple on 2005-10-24
What happens when you drop to a terminal and play with the settings using alsamixer?

I have a Soundblaster Live! 24 bit, and I noticed if the mixer settings are above 70 I get lots of clicking, hissing and the like.


I hope this helps!

---

### Post by some_random_newbie on 2005-10-24
I wasn't aware of that mixer.  Nifty.

Everything was in its 30s but I was able to enable some more speakers in it.

Unfortunately the clicking is still there.  This problem has me totally stumped. :(

---

### Post by some_random_newbie on 2005-10-25
wee bump

---

### Post by mikedtemple on 2005-10-25
One other thing you could try-  This also help drasticially improve my sound quality.

open a terminal and type 

sudo gedit /etc/asound.conf

Find the section that reads:

```

     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
        
```

Change the period_size to 2048
Change the buffer_size to 8192

You're basicially increasing the size of the sound buffer.  It fixed some latency issues for me.  Also try checking out this link from intangible about fixing all sorts of sound problems.  He saved my butt with that post-

[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)

I'm still a little new myself, I'm just trying to direct you to things that I know!

---

