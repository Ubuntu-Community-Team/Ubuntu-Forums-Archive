---
title: "alsa issues"
date: 2008-02-14
forum: General Help
---

### Post by malfist on 2008-02-14
I can't get my sound to work :(
Sometimes it will work, and then after a reboot it will stop. Gstreamer can't find devices and System->Pref->Sound doesn't list any devices.

Alsaconf can always find it (CMI8768 (supported by ALSA)) and configure alsa to use it but it never does.

It aways worked before, (I had an older CMI card), then I bought an Audugy SE and couldn't get it to work but I think I screwed alsa up trying to fix it. So I sent it back to newegg and put my old one back in and reinstalled alsa-base alsa-utils (purge option too). And it worked, but it always reset my mixer setting back to a default after a reboot.

Then I got my current card and randomly it won't detect it. The last time I fixed it by doing
```

sudo aptitude purge remove alsa-base alsa-utils linux-sound-base

```
And then reinstalling everything, but now that won't work.

I would appreciate any *any* help I get with this! I'm afriad I may have to reinstall ubuntu like I do for windows :(

Malfist

---

### Post by danwood76 on 2008-02-14
You could try compiling the alsa modules from source:
[http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install)

---

### Post by este on 2008-02-14
I know part of your problem.

K/X/Ubuntu only approve ALSA 1.0.14.  The CMI8788 isn't fully supported until .16 (.15 actually, but rewritten for 16). The full release of 1.0.16 just came out this month. I would grab the driver and tools.



I'm having my own issues with CMI8788 right now (system sound works with a small but noticeable delay) but no media players work. All say "Audio Unavailable - Device Busy".... I'm currently very stuck with it, infact I just screwed something up so bad I need to make a post about why my xsession isn't working.


I would recommend doing the alsa -l (lowercase L) once you get .16 installed.

---

### Post by malfist on 2008-02-14
I've tried installing from source but that just gives me hell. When will the newer alsa be backported?

---

### Post by malfist on 2008-02-14
I've never compiled a kernel :( Except with Gentoo, but that was easy.

---

### Post by malfist on 2008-02-14
May bad, it's actually:
01:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

---

### Post by este on 2008-02-14
Ah, probably a bit of difference there. I have no idea when that chip was supported.

But, one thing that would concern me is that compiling the alsa sources is simple.

./configure
make
sudo make install

Thats it. If you are having  problem there and your 7.10 is up to date there is something going on.

On that ./configure you could use the --withcards option, but I don't know the syntax off hand.

---

