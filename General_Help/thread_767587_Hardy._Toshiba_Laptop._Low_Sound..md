---
title: "Hardy. Toshiba Laptop. Low Sound."
date: 2008-04-25
forum: General Help
---

### Post by Roasted on 2008-04-25
So I just installed Hardy. Great! Now my sound works! I tried for DAAAAAAAYS to get my sound working on Gutsy. No luck. So I was instantly surprised and relieved to see Hardy supported my sound.

Then I turned up the volume.

What? It's maxed? Oh... it's maxed.

It's probably about 1/3 the volume level of what XP plays on the same laptop. Volume on Audacious AND the onboard audio are both maxed at 100%. 

What can I doooooooooo

---

### Post by natrixgli on 2008-04-25
Right click the volume icon on the panel and click 'open volume control' and check that the PCM level is up, and any other levels that seem pertinent. Also, you can enable more controls under Edit > Preferences.

See if that does it.

---

### Post by Roasted on 2008-04-26
That's already maxed.

---

### Post by JedV on 2008-04-26
I've noticed that my audio is quieter since changing to Hardy as well (although its a desktop computer - AMD64, on-board sound from Asus motherboard).

---

### Post by rstevens on 2008-04-26
Try changing the sound level using *alsamixer* in your terminal

---

### Post by exvision on 2008-04-29
I'm having the same problem on my HP laptop.  The sound is maxed out everywhere I can think of.. I tried the alsamixer.  But it's not very loud in Ubuntu, and is much louder in windows.

It was better before the recent upgrade....

---

### Post by redhound on 2008-05-05
Same problem for my Vaio VGN-T2XP/S ... Seems to be a general bug in 8.04 ...

---

### Post by halfhaggis on 2008-05-05
I had issues with no sound on my Asus laptop with gutsy.

I fixed it by editing /etc/modprobe.d/alsa-base -- at least on a laptop. This won't work for the desktop I don't think.

First -- have a look at the [debugging sound problems]("https://wiki.ubuntu.com/DebuggingSoundProblems") wiki page.

Then. If the suggestions don't help:
```
cat /proc/asound/cards
```
will give you the model of your sound card.

Then, open [Alsa Configuration Documentation]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt") and search for your card in the list.

```
lsmod|grep codec
```
might help you figure out which sound module you are looking for (will begin with "snd")

Once you've figured out which card and which module, you should have found a list of model names for the module and model.

For example, module snd-hda-intel lists cards ALC880, ALC260, etc. Under the cards are models "asus","lg","acer" etc.

Choose a model (asus, lg, whatever) that applies to your module and card. 

Then add the following line to the end of /etc/modprobe.d/alsa-base

```
options snd-hda-intel model=asus
```
Replace snd-hda-intel with your system-specific module, and asus with your chosen model.

Toshiba might not be the right one. For my Asus laptop, sound came on when I set model=lenovo. Weird.

I've paraphrased this from the [HdaIntelSound wiki page]("https://help.ubuntu.com/community/HdaIntelSoundHowto"). I didn't find it necessary to compile the latest alsa drivers from source.
I also don't know whether it will work or not if you have some other module running (not snd-hda-intel), but it's worth a shot.

---

### Post by spupy on 2008-05-05
Yeah, i got the same problem with my Toshiba. It fixes itself after a couple of hibernates/suspends, or some order of commands like (after sudo su):
```
# /etc/init.d/alsasound restart
# rmmod snd_hda_intel
# /etc/init.d/alsasound restart
# rmmod snd_hda_intel
# modprobe snd_hda_intel
```
But that is in Gentoo :) Don't know if Ubuntu uses init.d scripts.

---

