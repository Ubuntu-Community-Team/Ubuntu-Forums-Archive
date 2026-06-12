---
title: "Pulseaudio w/ Passthrough"
date: 2008-01-09
forum: General Help
---

### Post by ~LoKe on 2008-01-09
I've tried to get PulseAudio working on a couple of occasions, with almost complete failure each time.  With Hardy Heron, I've gotten further and now PA "works".  I get PA output with MPD/Totem/MPlayer.  The problem is that I can't get S/PDIF passthrough to my receiver, so no Dolby Digital/DTS.

**What the thread is for**
This thread is for explaining how you managed to get PulseAudio working with S/PDIF passthrough, or if you know how it should be done (for those who are educated on the topic of PA, but don't use s/pdif themselves).

**Video Players**
At this point, it doesn't matter which video player is used; they're all acceptable.  If you've gotten passthrough with PA, **please tell us how**.

**Preferred Information**
I'd appreciate it if you could provide as much information as you could about how you made it work.   Configuration files are critical here, mainly:
/etc/pulse/default.pa
/etc/pulse/client.pa
/etc/pulse/daemon.pa
~/.asoundrc

So...let's see if we can figure this all out, so a guide could be compiled in the future.

**Additional Threads**
I've been trying to get this sorted out for a while now, and I've made two threads on the topic.  They were for unrelated problems, but I thought someone might find the information useful.  These problems were resolved with the help of **rubicon**, and it wouldn't surprise me if he/she made an appearance here.

[COLOR="DarkOrange"][Connection Refused](http://ubuntuforums.org/showthread.php?t=660590)
[Missing Sink](http://ubuntuforums.org/showthread.php?t=660648)[/COLOR]

---

### Post by ~LoKe on 2008-01-09
So...either no one has gotten passthrough to work with PA, or no one feels like helping.  Aw.

---

### Post by dlegend on 2008-01-09
> **~LoKe said:**
> So...either no one has gotten passthrough to work with PA, or no one feels like helping.  Aw.

I think it's just most people just don't mess around with PulseAudio or don't even know what it is. At least that is the case with me. :lolflag:

---

### Post by ~LoKe on 2008-01-09
> **dlegend said:**
> I think it's just most people just don't mess around with PulseAudio or don't even know what it is. At least that is the case with me. :lolflag:

PulseAudio is supposedly a drop in replacement for ALSA and ESD.  It works beautifully in the sense that I can finally play multiple sounds at one (I can watch two movies, listen to music, and other audio stuff at the same time, not that I'd want to...).  One it gets passthrough working, it'll be most excellent.

---

### Post by fno on 2008-01-13
Well, I am trying and failing getting S/PDIF to work, unfortunately. Very close on giving up until Hardy comes out... :(

---

### Post by fno on 2008-01-13
This might have something to do with it:

[http:/pulseaudio.org/ticket/139](http:/pulseaudio.org/ticket/139)
[http://pulseaudio.org/ticket/167](http://pulseaudio.org/ticket/167)

---

### Post by falstaff on 2008-01-14
Hello,

I'm **VERY** interessted in this topic! I played around a bit with Gutsy and Pulseaudio, but not with the digital output. Since a few days i have got a AV-Reciever. I also have a dell Laptop with HDMI output (XPS M1330), but this output doesnt work on Linux (there is a bug report on LP, im waiting for this to be solved... btw, on vista it workes with VLC, but i have every minute a short interrupt). 

But I will buy a media pc anyway, which will have a S/PDIF output and HDMI, and there i would like to use pulseaudio, mpd and mythtv... And I would like to listen movies with ac3/dts sound... I will report if i can bring it to work as soon as i get the hardware (in about 1 or 2 weeks)...

bye
falstaff

---

### Post by Sharpeee on 2008-02-23
Hey. I'm very interested in this topic as well!

Any progress yet?

Cheers

---

### Post by rubicon on 2008-02-23
[quote=fno]http://pulseaudio.org/ticket/167[/quote]
Unless someone hacks PA and adds support for direct passthrough, it's quite like trying to swim in handcuffs... And the ticket is still here, no progress visible...

Frankly say, I have simple 4.0 card and can't test all that passthrough thingy, sorry.

[COLOR="Silver"](~LoKe: I may be a bit late, but isn't that '/etc/pulse/client.**conf**' and '/etc/pulse/daemon.**conf**'? :) )[/COLOR]

---

### Post by Sharpeee on 2008-03-04
I just found this post

[http://ubuntuforums.org/showthread.php?p=4451132](http://ubuntuforums.org/showthread.php?p=4451132)

It's awesome!!!

---

### Post by AdrianVeidt on 2008-05-01
This is a workaround. In your movie player, change the audio output driver from Pulse to Alsa, and you will be able to passthrough the digital stream without issue.
However, you will either get no sound or an error message if trying to play analog sound. So, when you want to play a movie with AC3 or DTS, which is the only situation you should be using passthrough for, change the driver (in Mplayer, for instance) and it will work, then change it back later.

---

