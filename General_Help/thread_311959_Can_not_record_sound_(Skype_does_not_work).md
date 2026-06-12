---
title: "Can not record sound (Skype does not work)"
date: 2006-12-03
forum: General Help
---

### Post by peletomi on 2006-12-03
Hello,

I am using Xubuntu Edgy, and I wanted to use Skype. Though I can hear the voice of the Skype test call I can not send any audio back. I tried to record also with arecord, this does not work either. 

I have two sound cards, one on the mainboard, and a Terratec Aureon 5.1 Fun, which is selected in the Skype preferences. I tried to raise the Mic settings in alsamixer (for the Terratec Card), precisely these are the settings:
Playback
Line = 100, Line-In = Line-In, Mic = 100, Mic Boost = 00 (I can not raise further), Mic-In Mode = Mic-In, Aux = 100
Capture
Mic = 100

Also it is worth noting, that I can hear my voice in the speakers as I speak into the mic.

I would appreciate any help! Thanks!

T.

---

### Post by peletomi on 2006-12-05
Hi!

I succeded finally! I used alsactl as follows:
```

sudo alsactl store
sudo vim /var/lib/alsa/asound.state
```

Then I changed the value of the 'Mic Capture Switch' to true. I additionally raised the Mic Capture volume. After this:

```

sudo alsactl restore
```

And it should work fine.

Cheers,
T

---

### Post by exjinn on 2007-01-03
thanks for this, it really saved me. :KS

---

### Post by Aurora on 2007-03-22
> **peletomi said:**
> Hello,

I am using Xubuntu Edgy, and I wanted to use Skype. Though I can hear the voice of the Skype test call I can not send any audio back. I tried to record also with arecord, this does not work either. 

I have two sound cards, one on the mainboard, and a Terratec Aureon 5.1 Fun, which is selected in the Skype preferences. 

T.

I have a similar problem; I did have it working but it suddenly stopped.  I then tried switching from the mic input to the line input, and I could hear myself in the phones, but it didn't record on the test call.  I went back to the mic input and the sound is very distorted in the phones; I think I blew the chip.

I am using a studio condenser mic through a Behringer Eurorack ub802 mixer, because it was the only way I had to connect the XLR connector on the mic cable to the mini phone jack on the computer.  I may have had the level up too much for the mic input (because the mixer output is really -10dB line level, not mic level) and fried it.  However, since the sound in the phones is still good when I use the line input, I think it may work if I can figure out how to get Skype to look for it.

How do I set that up?  There is no preference that I can find to choose between mic and line for the input..

Thanks,

Paul

---

### Post by csarlee on 2008-03-22
Tomi!

Ez nekem is bejött!!! :guitar:


Sorry for non-English...

Csarlee

---

