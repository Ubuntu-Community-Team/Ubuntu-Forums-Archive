---
title: "No sound from Sound Blaster Audigy!"
date: 2007-02-11
forum: General Help
---

### Post by Madmoose on 2007-02-11
Hello,

I've done a search around the forum, and I can't find anything. 

Maybe someone can help!


I'm have a Sound Blaster Audigy, and I'm not getting ANY sound. I've already gone in, and tried to make the EMU10K1 driver work by putting in

> 
sudo modprobe snd_emu10k1
.
It didn't work, so I looking into this thread.

When I typed alsamixer, and the sound thing came up I noticed that it says:

> Card: Intel ICH5
Chip: Analog Devices AD1985
View: [Playback] Capture all
Item: Master
Does this mean that it's looking at my MB's default card, and not my Sound Blaster Audigy?

Can someone please help me?! I'm about to pull out my hair! :(

---

### Post by Madmoose on 2007-02-11
Hello again, 

I got down and plugged the wires into my MB's card... IT IS WORKING! Ubuntu is pointing to the wrong card! 

How do I get it to point to my Sound Blaster Audigy, and not the on-board sound card... That I don't use.

Please help!

---

### Post by Madmoose on 2007-02-11
More info, 

 I looked under System> Preferences> Sounds, and it doesn't even list my card...

Does this mean I have no driver, but I keep reading that it comes with the live CD.

---

### Post by MrWally on 2007-02-13
I had this exact same problem with my card, I just went into the sound options and chose the selection that I knew wasn't my onboard.

But I still can't get surround sound to work. Ideas, anyone?

---

### Post by tubasoldier on 2007-02-13
I had the same issue but I disabled my onboard sound in my BIOS.

---

### Post by Madmoose on 2007-03-21
UPDATE:

I found it a while back ago, but if someone is also comes across this problem they can try this. 

I found out that you can switch your default care by

System---> Preferences--->  Sound---> Sounds---> Default Sound Card (It's the last tab on the bottom)

You can do [here]("http://www.ubuntuforums.org/showthread.php?t=161817&highlight=Sound+blaster") and get your surround keyed in.

---

### Post by slayerboy on 2007-03-21
you can do that..but I just disabled the onboard card in my bios.  It was much eaier to do that than go through and change settings that are useless if I don't use the card anyways!

---

### Post by Madmoose on 2007-03-21
Option #2 See:

> **slayerboy said:**
> you can do that..but I just disabled the onboard card in my bios.  It was much eaier to do that than go through and change settings that are useless if I don't use the card anyways!

\\:D/

---

