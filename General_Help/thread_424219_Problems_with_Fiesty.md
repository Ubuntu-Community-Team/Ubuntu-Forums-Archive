---
title: "Problems with Fiesty"
date: 2007-04-26
forum: General Help
---

### Post by mishranurag on 2007-04-26
Hi,

I just fresh installed Fiesty on my Desktop and in past I have used Breezy, Dapper and Edgy.  I am trying to use some programs but they do not appear to work (By the way, I didn't use them with older vsriosn either).

1. Audacity 1.2.6 --> It always shows me a error saying that it has trouble opening microphone.  I changed the sound driver to OSS from ALSA, and it worked once, but had a high pitched constant noise in background when I recorded something. I tried Audacity Beta, but it needs some dependencies to install from source code, and I was never able to do that.

2. GNUSound --> As soon as I click on record button xserver restarts.

3. JackEQ --> The program doesn't start.
Basically, I am having trouble with recording and editing podcasts.

4. Democracy Player --> It says it had trouble starting and then shuts down.

5. Compiz --> When I start compiz, the window decoration disappears and I cannot see the minimize, maximize, and close buttons.

I am surprised as to why couldn't these things be fixed before releasing Fiesty...

Anurag

---

### Post by mishranurag on 2007-04-26
Found out now that GNOME-RDP doesn't work either.  It fails to start and shows up some random errors. 

I am now seriously thinking of going back to Edgy.

---

### Post by mishranurag on 2007-04-27
For now, can anybody please tell me a good program for sound recording and editing that works in Fiesty?

---

### Post by strabes on 2007-04-27
Audacity is pretty much the best one. Sorry you can't seem to get it working.

---

### Post by itsjustarumour on 2007-04-27
Mishranurag,

Could you post up a basic list of your hardware specs so we can take a look?

The Compiz problem is definitely a bit of a "known issue" and has been for a long time for many people,  Remember that Compiz (and Beryl) still aren't at production standard yet, which is why Ubuntu decided not to include them by default in Fiesty.  But your audio issues.... thats a strange one!

---

### Post by mishranurag on 2007-04-27
I have sound cards built into mother board.  I am not sure how to get their specs, but I can tell that the other program using microphone is skype and it works perfectly fine without any configuration.

I got ArdourGTK and sweep working.  I can record and listen to my recording, but they are too complex for me.

Anurag

---

### Post by vrix on 2007-05-05
maybe you could try changing the project sample rate in audacity to 48000 (located bottom left) and record. it worked for me. hope this helps.

---

### Post by mishranurag on 2007-05-07
That fix did work. Thanks a lot.

Anurag

> **vrix said:**
> maybe you could try changing the project sample rate in audacity to 48000 (located bottom left) and record. it worked for me. hope this helps.

---

