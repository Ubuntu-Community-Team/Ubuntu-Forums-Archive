---
title: "Fresh Install, SPDIF!?"
date: 2007-12-30
forum: General Help
---

### Post by ~LoKe on 2007-12-30
Well...I believe I've destroyed this install well enough to warrant a fresh one.  I've decided to go 64bit this time, might as well take advantage of my quad core.

My question should be simple, though it rarely ends up that way.

I want SPDIF passthrough.  That's it.  That's all I've ever wanted and I can never get it consistently; it's ridiculous.

I've had spdif off and on for no apparent reasons, and lately I've been getting frustrated trying to make it work.  -ac hwac3 doesn't work in mplayer, vlc won't do it either, and xine won't even let me use alsa.  I know for a fact that my DVD's use DD 5.1 and DTS, as I've played them before and had true 5.1 (then stopped working, no one knows why).  I just want it to work, and keep working.

So, after a fresh install, what are the steps required in order for it to just..work.  I'll be using 64bit 7.10 (Gutsy).  My sound is integrated optical s/pdif into a receiver.  No software mixing, please.

**EDIT**: I'm proficient with the command line, so if you need to suggest that I compile something from source/SVN, or whatever, go ahead...I'll manage.  I'll take any consistent solution.  **Anything**.

---

### Post by ~LoKe on 2007-12-31
No rush on this, I suppose. Can't even get 64 7.10 installed. :confused:

---

### Post by hbj on 2007-12-31
Hi,

I'm new to this but will try to help.  Do you have any sound at all from SPDIF input to your receiver?  I just got mine working - all I had to do was move the slider for IEC958 Playback to the zero position (of four possible) and sound from SPDIF worked.  Haven't tried passthrough for surround sound on movies or anything else yet.

Running 7.10, i386, Kubuntu.

On edit:  I have a 5.1 system.  Front left and right are working, tested with the wav file found [here]("http://www.halfgaar.net/resources/chan-id.zip").  Have tried:

aplay chan-id.wav   : Front left and right work
aplay -D surround51 chan-id.wav  : Front left and right work, but are much louder and at a higher pitch (I guess 48000 Hz playback instead of 44100) and don't sound right.

Haven't gotten surround speakers working yet...

---

### Post by jayde6 on 2007-12-31
To get spdif to work for me (same setup onboard straight to reciever) I had to make a .asoundrc file  in my home directory. This is in mine,

```
 
pcm.!default {
        type plug
        slave {
                rate 48000
                pcm "spdif"
		format S16_LE
        }
}

```

I also had to set my reciever to manual signal detection rather than automatic signal detection.
Hope this helps.
~Jennifer

---

### Post by ~LoKe on 2007-12-31
Well...installed 64bit Gutsy, installed mplayer, libdvdcss2, w64codecs, and added that block to ~/.asoundrc, and already my DVD's are playing over s/pdif and coming up 5.1 and 6.1 DD on my receiver.  Success! 

Thanks a lot, Jennifer!

---

### Post by RJ Hythloday on 2008-01-13
I had dapper for a day and managed to get the spdif working after installing alsamixer and changing the IEC958 as I had found in several forums.

I now have gutsy and am not able to figure out any sound, I tried the a.asoundrc file like Jennifer suggested also but still no luck.

I am using a turtle beach soundcard optical>reciever.

---

