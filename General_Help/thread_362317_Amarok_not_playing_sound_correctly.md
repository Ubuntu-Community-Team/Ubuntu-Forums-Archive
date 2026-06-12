---
title: "Amarok not playing sound correctly"
date: 2007-02-15
forum: General Help
---

### Post by ozw on 2007-02-15
I'm not sure if it's Amarok, or xine, or Ubuntu's handling of my sound card, but my sounds are not playing correctly.  When I play music in Amarok, something sounds off, and I wasn't sure why, but then I played a song and the singing on an entire verse was completely missing, so I'm thinking it's just not playing a certain channel or something.  How would I go about fixing this?

I'm running Kubuntu Edgy if that matters.

---

### Post by g8m on 2007-02-15
Not sure I understand your problem.

Open konsole en run alsamixer and check if all channels are unmuted and the volumes are up.

In amarok go to preferences - engine and choose the audio configuration. (stereo, surround, 5.1  or 7,1).

Instead of alsamiser you can also try kmix, but i prefer alsamixer. Once I noticed with kmix that the volumes where up, but with alsamixer I could see that the left back channel was up but the right back was down. 

But missing voices completely, that sounds more like broken streams.

---

### Post by ozw on 2007-02-15
Believe me, I'm not sure I understand it either, heh.  KMix is no help.  Changing audio config is no help.  Alsamixer only shows "Master" and "Master mono."  Both seem to be working.  But I dunno.  I think it's something like, it's only playing the left or right channel and not both because I've had this problem on my mp3 player when one speaker in my car broke, and when I had one headphone break.  Do I need new sound drivers or something?

Edit: It doesn't work in Kaffeine either so it's not just Amarok.  Either it's xine, or more likely, Ubuntu.

---

### Post by g8m on 2007-02-15
Only mono. Hmm, that's a driver problem if you're card is stereo.
Or there is more than 1 card and the wrong one is selected.

   cat /proc/asound/cards

Alsamixer shows wich card/chip it's using.

maybe [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) can give some insight.

---

### Post by ozw on 2007-02-15
cat /proc/asound/cards produces the following:

```

 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at 0xfeb7fa00, irq 201
 1 [camera         ]: USB-Audio - USB camera
                      USB camera at usb-0000:00:1d.2-2, full speed

```

Also...under alsamixer...the sound is from "headphone" instead of "master" for some reason.  I think my sound card is a Creative Labs Soundblaster Live! 5.1 emu10k1x....so it looks like I have the wrong driver installed?  I guess I need to figure out how to install the correct driver now.

---

### Post by ozw on 2007-02-15
Alright, it seems like all I need to do is upgrade ALSA.  I'll try to figure out how to do that.  Hopefully that should work.

---

### Post by ozw on 2007-02-18
Oh god.  You do not understand how stupid I feel right now.  But I'll let you all know what the problem was so you can laugh at me.  The cord that connects my computer to my speakers was loose.  Hah.  Of course it had to come loose coincidentally at the same time I installed Kubuntu.  And of course I totally messed everything up by trying to reinstall ALSA from scratch and now I have no sound at all and am probably going to have to try a fresh install.  #-o  Haha at least I can laugh about it.

---

### Post by Maestro23 on 2007-02-18
> **ozw said:**
> Oh god.  You do not understand how stupid I feel right now.  But I'll let you all know what the problem was so you can laugh at me.  The cord that connects my computer to my speakers was loose.  Hah.  Of course it had to come loose coincidentally at the same time I installed Kubuntu.  And of course I totally messed everything up by trying to reinstall ALSA from scratch and now I have no sound at all and am probably going to have to try a fresh install.  #-o  Haha at least I can laugh about it.

How many people forget to check the wires/connections first.:) 

Just get you a stiff drink and laugh about it for a few minutes.:guitar: 

Good luck man.

---

