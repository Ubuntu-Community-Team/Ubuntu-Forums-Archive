---
title: "sound not working in tc:e -- i tried the normal remedy"
date: 2007-05-08
forum: General Help
---

### Post by glenmo on 2007-05-08
i did the 

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss


thing, but sound still doesn't work with tc:e and also enemy territory...

has anything else worked for anyone?  

I have a pentium 4, chaintech 9cjs zenith mobo wih envy24 sound integrated.  i have headphones plugged into the back and my stereo plugged into the front audio jack.  i can listen to music, flash, dvds, audio cds, and i get sound from videos -- the only thing that doesn't work is tc:e

i'm gonna try another game and see what happens...

---

### Post by abc123456 on 2007-05-08
Ln -s wherever the real snd card is link it to where tc wants it.:)

---

### Post by glenmo on 2007-05-08
i'm not sure i understand how to do that:

how can i find out where tc:e wants it?

how can i find out which is my real soundcard?

lspci brings back this:
03:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)


applications > sysinfo doesn't show me anything about my sound card...

---

### Post by glenmo on 2007-05-14
bumping... i still don't know how to fix this.

---

### Post by glenmo on 2007-05-21
i started a thread on the tce forums... 
[http://www.truecombatelite.net/forum/viewtopic.php?p=68277#68277](http://www.truecombatelite.net/forum/viewtopic.php?p=68277#68277)

no sound not working in tc:e

---

