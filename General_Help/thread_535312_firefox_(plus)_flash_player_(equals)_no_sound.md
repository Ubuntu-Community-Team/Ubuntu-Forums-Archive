---
title: "firefox (plus) flash player (equals) no sound"
date: 2007-08-26
forum: General Help
---

### Post by djcrash1981 on 2007-08-26
Ok, now i been looking in the forums a solution for my problem.
I've been trying diferents solutions.
[http://ubuntuforums.org/showthread.php?t=205449&highlight=flash+player+no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=flash+player+no+sound)
[http://ubuntuforums.org/showthread.php?t=452882&highlight=flash+player+no+sound](http://ubuntuforums.org/showthread.php?t=452882&highlight=flash+player+no+sound)
[http://ubuntuforums.org/showthread.php?t=255422&highlight=flash+player+no+sound](http://ubuntuforums.org/showthread.php?t=255422&highlight=flash+player+no+sound)
[http://ubuntuforums.org/showthread.php?t=510634&highlight=flash+player+no+sound](http://ubuntuforums.org/showthread.php?t=510634&highlight=flash+player+no+sound)
[http://ubuntuforums.org/showthread.php?t=428979&highlight=flash+player+no+sound](http://ubuntuforums.org/showthread.php?t=428979&highlight=flash+player+no+sound)
[http://ubuntuforums.org/showthread.php?t=263908](http://ubuntuforums.org/showthread.php?t=263908)
[http://ubuntuforums.org/showthread.php?t=58691](http://ubuntuforums.org/showthread.php?t=58691)

But none of them has given a solution to my problem.

So I'm asking to the goods of ubuntu how can i solve this?

Some of my stats are:

Ubuntu Festy Fawn
Firefox 2.0.6 (from repositories)
Adobe Flash player (from page [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux))

I have two sound cards:
[email]djcrash@sirius:/tmp/.esd[/email]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1370/1 [ES1370 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1370/2 [ES1370 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

My default card is a Sound Blaster PCI 128 (Card 0) a little bit old but very good for what i want.

I have no troubles at all listening music or videos inside of ubuntu with Rhythmbox or Totem.

I'm deseperate because I'm a big fan of [www.youtube.com](www.youtube.com) and now i can't heard a thing.

By the way this was working fine until i did an "recommended" update.

Thanks for all and I hope someone can help me out with my problem.

;'(

---

### Post by Libre on 2007-08-29
I can't get flash sound to work on Firefox either. I have tried changing none to aoss, but that doesn't do anything. Sound works fine everywhere else.

I also have an Ensoniq sound card.

---

### Post by jusmurph on 2007-08-29
Have you tried disabling your onboard sound? Try in the mobo bios...

The general idea is to make sure alll sounds are directed to your sound card...

---

### Post by djcrash1981 on 2007-09-01
Yes, i already try it, and its all the same

---

### Post by Libre on 2007-09-02
> **jusmurph said:**
> Have you tried disabling your onboard sound? Try in the mobo bios...

The general idea is to make sure alll sounds are directed to your sound card...

Still not working.

---

### Post by djcrash1981 on 2007-09-20
Anybody have more ideas or should i reinstall de PC?????

Please help!!!!!!!!!!!! :'(

---

### Post by mitchlinux on 2007-09-22
I was also very frustrated until I found this. 

sudo asoundconf list

you should see a list of devices. i.e ICH Headphones or whatever you have connected. Then type:

sude asoundconf set-default-card "you device"     

without the quotes please.

Then restart by using ctrl+alt+backspace login again and try youtube again.

I tried everything before and nothing worked. This worked marvelously.

---

### Post by dlh1 on 2007-09-28
Thanks.  After trying several other suggestions, this fix worked for me.
__
dlh

---

### Post by soelk on 2007-09-29
> **mitchlinux said:**
> 
sudo asoundconf list

you should see a list of devices. i.e ICH Headphones or whatever you have connected. Then type:

sudo asoundconf set-default-card "you device"     

without the quotes please.

Then restart by using ctrl+alt+backspace login again and try youtube again.

Yes, finally! This method solved it for me on the 7.10 beta. Thanks.

---

### Post by wardyp on 2007-10-19
Thank you soo much! Tried loads of fixes but this is the one that worked for me.

I finally feel like I have a complete system.. bye,bye XP..

---

### Post by SCGreg on 2007-10-19
> **mitchlinux said:**
> I was also very frustrated until I found this. 

sudo asoundconf list

you should see a list of devices. i.e ICH Headphones or whatever you have connected. Then type:

sude asoundconf set-default-card "you device"     

without the quotes please.

Then restart by using ctrl+alt+backspace login again and try youtube again.

I tried everything before and nothing worked. This worked marvelously.

nice one - worked for me too! :)

---

### Post by henderbops on 2007-10-23
Finally the only one that worked.. i've tried allsorts, a lot of which mentioned above.

---

### Post by ghr on 2007-10-24
FINALLY.....able to hear sound in flash...thank you.

---

### Post by diablozx9 on 2007-10-29
THAT WORKED,,,, THANKS.

I tried everything.. This one worked.   Cheers.

---

