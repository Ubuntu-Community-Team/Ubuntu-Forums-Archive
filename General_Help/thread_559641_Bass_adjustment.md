---
title: "Bass adjustment"
date: 2007-09-25
forum: General Help
---

### Post by kulturfenster on 2007-09-25
hi everybody,
i just installed ubuntu 7.04.

how can i adjust the bass? Its pretty urgent since the neighbor is always complaining about it! ;) :guitar:

thanks for every advise!

---

### Post by SOULRiDER on 2007-09-25
What music player are you using? Most music players have Equalizaers.

---

### Post by kulturfenster on 2007-09-25
i am using Rhythmbox 0.10.0.

Yeah, i thought so, too. Unfortunately i couldnt find anything. All i could adjust was the volume..
How about "inside" of ubuntu?

---

### Post by youbaba on 2007-09-25
Well try running "alsamixer", mine has got an EQ.

---

### Post by kulturfenster on 2007-09-25
i just started using Linux..

is there an easy way to get it?

---

### Post by Jose Catre-Vandis on 2007-09-25
Open a terminal
type
```
alsamixer
```

L/R arrows to move, TAB to change between playback/capture/all, up/down arrows to adjust

mine doesn't have EQ though, unless i am missing something

---

### Post by timzak on 2007-09-25
It depends on your sound card.  I have a machine with onboard sound that has no adjustments for bass or treble (even in Windows).  But my old Sound Blaster Live! card (the original version) does have bass/treble adjustments built into the hardware and both Creative Labs Windows drivers as well as Alsa drivers in Ubuntu have this feature enabled, so I am able to adjust bass/treble through the software.  If you don't have software access, you are limited to any adjustments on the speakers themselves.

Just double-click the speaker icon on your panel and it should show you available adjustments.  I think I had to tick on "Tone" to get the bass and treble adjustments to appear.

---

### Post by matt_risi on 2007-09-25
I've always wished for this idea of a system-wide EQ.. anyone who can come up with an existing program would kick some serious *** in my books.

---

### Post by kulturfenster on 2007-09-25
well, that looks pretty much like when you double click the loudspeaker icon on the panel.  Its very similar to a EQ. No bass control, tough..

---

### Post by timzak on 2007-09-25
> **kulturfenster said:**
> well, that looks pretty much like when you double click the loudspeaker icon on the panel.  Its very similar to a EQ. No bass control, tough..

This is what I was talking about.  I do have a bass control here, but I think it is because my sound hardware has support built in for it.  Also, like I said in my previous post, I think you have to "enable" the bass/treble controls by ticking on another box...maybe the one labeled "tone"?  I'm on a Windows machine right now so I cannot check.  But go through the various menus and start ticking on boxes that don't have checks in them already and see if you can get it to show up.

BTW, what is your sound card?  Or is it built into the motherboard?  Have you ever run Windows on your system and if so, were you able to adjust bass in Windows?

---

