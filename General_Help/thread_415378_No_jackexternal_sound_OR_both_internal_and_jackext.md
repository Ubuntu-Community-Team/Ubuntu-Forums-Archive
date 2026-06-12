---
title: "No jack/external sound OR both internal and jack/external sound"
date: 2007-04-20
forum: General Help
---

### Post by Reschat on 2007-04-20
Firs: Laptop (Acer Travelmate 2480) - Ubuntu Feisty Fawn - Internal and external (jack) speakers

I have a problem after upgrading to Feisty Fawn. At first I didn't have any sound but after trying this:

**sudo gedit /etc/modprobe.d/alsa-base**
and inserting this line:
> options snd-hda-intel model=auto

I now have sound. But now the way I like it.
With my external speakers pluged in jack there are still sound comming out of the internal speakers (like before). The problem is that there in **alsamixer** is no "surround" volume setting which there was before (in Edgy - or when the sound didn't work) to control the volume of the internal speakers.
And now the "front" volume setting is not just for en external speakers (like it was before) - but for both the external and internal speakers (but this is NOT a problem - since I always had it at max anyway).

But I would like a setting to turn down (or off) the volumen of the internal speakers in alsamixer (or OSS?)

I hope someone can help me.

By the way: There are no Xes out of "alsa-utils" in "sudo sysv-rc-conf". But I really don't think there was that in Edgy either.

---

### Post by Reschat on 2007-04-20
I really need this so I was hoping that someone had an idea or two.

Please...

---

### Post by silverglade00 on 2007-04-21
Try changing it to model=acer. I believe that acer has their own model type that needs it. You might also try 3stack or laptop if that doesn't work.

You might also need to compile and run the latest alsa drivers. I had to do that for my HP laptop. It wouldn't mute the speakers when I plugged the headphones in.

---

### Post by Reschat on 2007-04-21
I have tryed some diffirent things. But model=acer actually worked.

Thank you so very much. :) Sometime the simple solution is the right one.

---

### Post by dannica12345 on 2007-04-22
I have the acer aspire 3680 laptop
when i plug in my external speakers, I HAVE NOTHING!
i did a while ago today but then i rebooted and poof its gone. i think i had a virus or sumthing that was doing good instead of bad, whatever it was it is gone now:(
its been like this since the day i got my comp and im runing xp mce.
im sick of having to use my ipod to play music throught my speakers.
and when i watch movies all i have is the stupid speakers it came with, which i can whisper over and still hear my self even at the loudest.
pleeeeaaaase someone help!

and i dont normally post on forums, so if me posting here was wrong, im sorry, but its almost the same prob, so i think it should be ok

Diana

---

### Post by dannica12345 on 2007-04-22
P.S.
my email address is [email]diana_vishloff@yahoo.ca[/email]

---

### Post by Reschat on 2007-04-22
dannica12345 - Which version of Ubuntu do you have?

And if you use Feisty Fawn then try what I wrote in my first post in this thread - but maybe with "model=acer" instead of "model=auto".

---

### Post by Reschat on 2007-04-22
I need some help again. silverglade00 ?
Same thing.

I still have model=acer - but after a crash it dosn't work anymore.
And if I set model=auto it does like it did before. Both internal and external at the same time.

My computer crashed while I was using xev and pressed the "play/pause" button. My music player (Listen) played and pause again and again and again. I don't really know why. 
Nothing responded so I had to press (and hold) the turn on/off button on my computer. And now no external sound.

Anybody?

---

### Post by Reschat on 2007-04-22
It is actually the same problem as to begin with (something have changed the ACER-settings). 
But the solution before was:
```
options snd-hda-intel model=acer
```

But like I said - something was changed. It dosn't work anymore. It is the same with:
```
options snd-hda-intel model=laptop
options snd-hda-intel model=xyz
options snd-hda-intel model=3stack
```
(one at the time)

So does anybody know how to "reset" the ACER-alsa-settings or something?
I really need this. model=auto still have sound on both internal and external speakers - but how can I then use a headset when the sound is still comming out of the internal speakers?

Any ideas please. Thanks.

---

### Post by Reschat on 2007-04-24
I don't get it. But suddently it works.

This morning (Denmark) I tryed what I did yesterday and how the sound works like before (good!).

I did this:

 - Reinstall all app. with the word "alsa" in it

 - Removed:
```
options snd-hda-intel model=acer
```
from /etc/modprobe.d/snd-hda-intel.modprobe

 - Changed:
```
options snd-hda-intel model=acer
```
to
```
options snd-hda-intel model=laptop position_fix=1
```
in /etc/modprobe.d/alsa-base

 - And then finally ran:
```
 kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*) ; sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') && sudo modprobe snd-hda-codec && sudo modprobe snd-hda-intel model=acer
```

If it works after a restart - I don't know. I'll edit this post to tell later after I'd had the time to try.
Thanks everyone for trying :)

*EDIT* Works after restart.

---

### Post by dannica12345 on 2007-04-24
why do u assume i would have ubuntu and isnt it just a website and what is fiesty fawn? if i dont know what itis im NOT downloading it. and i dont even know what they do, nowhere in there titles doesit say sound card driver. so what is it then? and my problem is not the same as that buddys problem, he gpot sound from BOTH sets of speakers, i only get 1 set, sumtimes other set works like today and yesterday
but w/e ur just gonna tel me t use buntu w/e it is and that fiesty fawn thning


so in repsonse to your answer, i dont have ubuntu

---

### Post by Reschat on 2007-04-25
dannica12345 - I just asumed that because this is "Ubuntu forums" (ubuntuforums.org). 
Feisty Fawn is the newest version of Ubuntu.

But I don't know much about Windows - so I can't help. Sorry.

---

### Post by zekebaker on 2007-04-25
I am running Feisty too, had a dapper->Edgy updated system just got Feisty on it

It's a Travelmate-2480-2247 sound used to work now doesn't. Tried everything you suggested, no luck. 
 kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*) ; sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') && sudo modprobe snd-hda-codec && sudo modprobe snd-hda-intel model=acer

Didn't help. If you can help please e-mail me at jorgen x uoguelph x ca thanks!

Here is my .etc/modprobe alsa-base file
 kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*) ; sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') && sudo modprobe snd-hda-codec && sudo modprobe snd-hda-intel model=acer
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# options snd-hda-intel model=auto/acer Added from internet information
options snd-hda-intel model=acer
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by Reschat on 2007-04-26
I don't know what you should try. But here is my /etc/modprobe.d/alsa-base file:

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=laptop position_fix=1

I hope it helps.

Why do you have 
 > kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*) ; sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') && sudo modprobe snd-hda-codec && sudo modprobe snd-hda-intel model=acer
In your file?

Instead of
> options snd-hda-intel model=acer
then try
> options snd-hda-intel model=laptop position_fix=1

Or just do as I wrote here: [http://ubuntuforums.org/showpost.php?p=2521368&postcount=10]("http://ubuntuforums.org/showpost.php?p=2521368&postcount=10")

I hope it works for you.

---

### Post by larsemil on 2007-05-14
i have the problem that after i have jacked in something, earphones, speakers or whatever in the line out/headphone plug i dont get any sound in the internal laptop speakers afterwards. even if i plug the headphones out. before i had sound in both wich i liked alot.

---

### Post by Reschat on 2007-05-21
I think that everytime my computer crashes while playing music it does something not good to my  snd-hda-intel.

But every time I can edit:
/etc/modprobe.d/alsa-base
and get it to work again.

I have used these:
[b]
options snd-hda-intel model=acer

options snd-hda-intel model=laptop position_fix=1

options snd-hda-intel model=laptop-eapd[/b]

And next time I'll try:

**options snd-hda-intel model=laptop-v71**

---

### Post by staceyofthelamp on 2007-12-20
what does these commands do, a very helpfull person in #alsa sorted me out with 
options snd-hda-intel model=3stack

before only external worked now its only internal, im going to try playing around with some of the commands in this thread. does anybody know what they do?

---

