---
title: "soundcard not detected"
date: 2008-03-10
forum: General Help
---

### Post by patree on 2008-03-10
my sound card was working great until about 20 minutes ago when  decided to get the newest update.. i restarted my computer and cannot even open the volume controls.
i just get this message: No volume control GStreamer plugins and/or devices found.

also heres what i get from alsamixer:
$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device


for some reason my card isnt being detected anymore... can anybody provide me with a siple way to reinstall my soundcard?

---

### Post by thirunavukkarasu on 2008-03-10
Hi, 

Just reinstall the linux-generic package and see. 

With regards
Thiru.S

---

### Post by Dithers on 2008-03-10
what soundcard is it?

---

### Post by patree on 2008-03-10
hello 
i tried installing linux generic packages and nothing changed.. and i dont know how to find out my soundcard because according to my computer i dont have one anymore... ?

it says that i need gs streamer plugins, i tried searching for them but there are so many i dont know the correct ones to install to make things work

---

### Post by Junglizer on 2008-03-10
try running ```
alsaconf
``` from the CLI.

---

### Post by erginemr on 2008-03-10
Please refer to:
[http://ubuntuforums.org/showthread.php?t=714635](http://ubuntuforums.org/showthread.php?t=714635)

and pay special attention to the link I gave at post no. 8. (It will work if your sound card is onboard with a HDA Intel chip.)

But before that, a few questions:

1- Are you using a Laptop? If so, what is its brand?

2- Are you using an on-board sound card or an external PCI card? If the latter is the case, what is its brand?

3- To try to identify your audio chip, you may try:
```
aplay -l
```
and
```
lspci | grep -i audio
```
from a terminal. Yet, since your sound card is not detected, you will have no useful output from these commands.

4- Boot from the Ubuntu Live CD, check if your sound is working and re-run those two commands above.

---

### Post by Feivel on 2008-03-10
I am running Hardy Heron and i had no problem with sound until this morning (after the update).

aplay -l gives error 205:no sound card detected

lspci | grep -i audio gives 00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

I followed [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) as far as reinstalling the ALSA drivers but no luck. Anybody have any ideas. I really hate to boot into super slow windows just to listen to music.

BTW, booting into windows my sound works and also working when i boot off the LiveCD.

---

### Post by Feivel on 2008-03-10
> **Feivel said:**
> I am running Hardy Heron and i had no problem with sound until this morning (after the update).

aplay -l gives error 205:no sound card detected

lspci | grep -i audio gives 00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

I followed [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) as far as reinstalling the ALSA drivers but no luck. Anybody have any ideas. I really hate to boot into super slow windows just to listen to music.

BTW, booting into windows my sound works and also working when i boot off the LiveCD.

Anybody??

---

### Post by erginemr on 2008-03-10
To begin with, you are running Hardy, an alpha/beta OS, and you should expect such hiccups.

You have already tried:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

I presume. This trick has been reported by many users as working in Gutsy, but I don't know whether it will also work for Hardy.

---

### Post by erginemr on 2008-03-10
Alternatively, boot into the Live CD, grab the file "/etc/modprobe.d/alsa-base" to a pen drive.

Then, boot normally, and compare the contents of the file you grabbed from the Live CD with the existing file "/etc/modprobe.d/alsa-base" in your system, esp. the line:
```
options snd-hda-intel model=.....
```

Try to back up your original file first with:
```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.mybackup
```
and replace it with the one you have fetched from the Live CD. See what happens.

---

### Post by starNIX on 2008-03-10
Same problem here.  I'm guessing alot of people are seeing this.  You may want to report the bug.  That way it will be fixed in the next day or so.

---

### Post by Michl on 2008-03-10
Same problem here in Hardy after the most recent update.  I am assming
it is related to the alsa update.  In any case, I am assuming that in the
next couple of days this will be ironed out with the next set of updates.
Someone should file a bug report, but I don't have the time today.

---

### Post by Feivel on 2008-03-10
> **erginemr said:**
> Alternatively, boot into the Live CD, grab the file "/etc/modprobe.d/alsa-base" to a pen drive.

Then, boot normally, and compare the contents of the file you grabbed from the Live CD with the existing file "/etc/modprobe.d/alsa-base" in your system, esp. the line:
```
options snd-hda-intel model=.....
```

Try to back up your original file first with:
```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.mybackup
```
and replace it with the one you have fetched from the Live CD. See what happens.

I understand there will be some problems with HH. This is also happening on Gusty according to the OP. I checked the /etc/modprobe.d/alsa-base on this install BEFORE I grabbed a copy of the LiveCD boot. The only difference was in the first line under the options section which was...

```
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
```

where under the Hardy install it was...

```
# Prevent abnormal drivers from grabbing index 0
options bt877x index=-2
```

There was no line beginning {code]options snd-hda-intel model=....[/code]

It read...

```
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

BTW, the version of the LiveCD I am using is 7.10. The alsa-base file should be the same for Hardy shouldn't it?

ETA - When I do a dmesg  inbetween all the unknow symbol lines I find a disturbing entry...

```
[   55.611946] nvidia: module license 'NVIDIA' taints kernel.

```

---

### Post by Feivel on 2008-03-10
Hmm....did another update and now it is detecting my realtek audio. I am going to go through LordRaiden's tutorial again.

---

### Post by Feivel on 2008-03-10
Success...sort of :)

I got my sound working BUT There is a background hiss i have to get rid of BEFORE I throw a heavy object through my monitor.

ETA - Turned my master volume down a tad and it works great.

---

### Post by erginemr on 2008-03-11
Great! For the hissing, you may also try "alsamixer" and set the PCM volume level to zero dB gain, as higher values can sometimes distort the sound.

---

### Post by Feivel on 2008-03-11
> **erginemr said:**
> Great! For the hissing, you may also try "alsamixer" and set the PCM volume level to zero dB gain, as higher values can sometimes distort the sound.

I got sound working in RythmBox and it sounds much better than ALSA did. The only thing not working is Last.FM. Odd since google video and youtube are fine but at the moment, I am not even gonna think about messing it up.

---

