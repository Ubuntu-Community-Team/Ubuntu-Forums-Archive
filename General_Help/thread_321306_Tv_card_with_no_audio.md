---
title: "Tv card with no audio"
date: 2006-12-18
forum: General Help
---

### Post by IndigoMontoya on 2006-12-18
I did a fresh install of edgy and can not get audio from my Hauppauge TV card anymore.   It was working in dapper.  I believe (but may be wrong) that I had to change some configuration option to get it working previously, but I don't remember what (or even if I actually did this).  The audio out on the card is still connected to the audio in on the sound card and all my other audio is working.  It is a Hauppauge TV-radio 848 based pci card.  Any thoughts?  

lspci |grep bttv
```

bttv                  176116  1 
video_buf              27652  1 bttv
ir_common              28548  1 bttv
compat_ioctl32          2432  1 bttv
i2c_algo_bit           10376  1 bttv
v4l2_common            17280  3 tuner,msp3400,bttv
btcx_risc               6280  1 bttv
tveeprom               16144  1 bttv
i2c_core               23424  9 i2c_ec,i2c_viapro,tuner,tvaudio,nvidia,msp3400,bttv,i2c_algo_bit,tveeprom
videodev               10752  3 spca5xx,bttv

```

---

### Post by scoon on 2006-12-18
hey there, 

Tweak the settings with alsamixer.  Maybe that channel got muted for the ugrade.

-scoon

---

### Post by IndigoMontoya on 2006-12-18
Hey,

Thanks for the reply.  I have tried that too.  I have turned everything on and fully up and it still does nothing.  

~Scott

---

### Post by fragos on 2006-12-18
Assuming your card is like the WinTV Go, double check the audio cable.  Mine has a tendency to be pulled out if I moved my box to plug in a new USB device.

---

### Post by IndigoMontoya on 2006-12-18
It is not the wintv-Go.  It is a PCI based wintv-radio.  I have gone through and messed with the audio out cable.  

Also, it may be worth nothing I have the motherboard soundcard and another soundcard installed on this system.  I have tried all the combinations of plugging the audio out of the tv card into the different sound cards and switching which sound card is being used.  Nothing has worked.  

Thanks for the comment though

~Scott

---

### Post by scoon on 2006-12-19
Hey there, 

Check w/ lspci that it is actually recognized.  Also check dmesg to be certain that there isn't a problem.  It could also be that not all the modules needed for the card to work are getting loaded and that's why the sound doesn't work.  I have an ATI tv-wonder card and if the card type doesn't get selected when the module loads, I don't get any sound and video is only in B&W.

-scoon

---

### Post by IndigoMontoya on 2006-12-31
Thanks to everyone who gave some input.  The problem was on my end.  Short answer:  I fixed it.  

Long answer:  I was speaking with an old friend over the holiday and while I mentioned the problem I also though of the possible issue.  As I mentioned, I have both onboard audio AND another soundcard.  I tried all permutations of which card to use, but when I disabled the onboard audio through the bios, everything magically worked as expected.  I guess it was silly to not try that first.  

so it is working. Thanks to all that helped.  now time to get MythTV up and running as well.   EEK!

---

