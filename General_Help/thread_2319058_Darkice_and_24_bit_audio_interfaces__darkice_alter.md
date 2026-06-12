---
title: "Darkice and 24 bit audio interfaces / darkice alternative / Creative E-MU"
date: 2016-03-31
forum: General Help
---

### Post by funkytwig2 on 2016-03-31
Hi, ive been trying to get darkice working with a Creative E-MU audio interface but dont think it will work.  It seems darkice does not work with 24 bit audio interfaces, a real shame.

Maybe someone has got it working, if so advice would be great.

Alternatively was wondering what other streaming clients there were that can be used with shoutcast?

Ben

---

### Post by QDR06VV9 on 2016-03-31
I think their set-up to use
> #bitrateMode    = cbr (do not use vbr) #bitrate        = 16 or 32 (16 for mono feeds, 32 for stereo feeds)
Have you tried with 32 bit?

---

### Post by funkytwig2 on 2016-03-31
Tried and got same error 

[I][B]DarkIce: LameLibEncoder.h:115: specified bits per sample not supported [32]

I wanted to use a audio interface with levels but all the ones I can find are 24bit;(.
[/B][/I]

---

### Post by QDR06VV9 on 2016-03-31
Sorry to hear that...but you saved me some time I was also going to install it and give it a go.
But i see that the quality is not my cup of tea.
Regards

---

### Post by funkytwig2 on 2016-03-31
It may just be me, ou may have better luck.

i did read some reviews and both the build quality and audio quality seemed very good.

ben

---

### Post by funkytwig2 on 2016-04-01
OK, got it working, used .~/asoundrc
    [INDENT]pcm_slave.sl3 {
         pcm "plughw:1,0"
         channels 2
         rate 44100
      }
      
      pcm.complex_convert {
         type plug
         format S16_LE
         slave sl3
      }
    [/INDENT]     And the darkice.cfg input section is 
    
    [INDENT][input]
      device          = plughw:1,0    # Alsa soundcard device for the       audio input
      sampleRate      = 44100     # sample rate in Hz. try 11025, 22050       or 44100
      bitsPerSample   = 16
      channel         = 2         # channels. 1 = mono, 2 = stereo
    [/INDENT]     Ben

---

### Post by QDR06VV9 on 2016-04-01
Good Job Ben..:D
And thanks for sharing your solution.
Kind Regards

---

### Post by funkytwig2 on 2016-04-03
Actualy the whole [COLOR=#000000]~/asoundrc  is probably not necessary, think it is the plughw bit that did it.[/COLOR]

[COLOR=#000000]Ben[/COLOR]

---

