---
title: "Phantom Headphone Audio"
date: 2016-01-03
forum: General Help
---

### Post by nebhead772 on 2016-01-03
I'm running into an issue similar, if not he same as in this previous post: [http://ubuntuforums.org/showthread.php?t=2132324](http://ubuntuforums.org/showthread.php?t=2132324)

It was never solved and then an some point locked, so I was hoping to re-open the discussion.  I recently re-installed Ubuntu 14.04.3 and noticed that the audio sounds somewhat glitchy when watching a video.  I then noticed that the sound settings dialog would occasionally flicker with a headphone connection, then go away even though no headphones were plugged in.  After plugging in a pair of headphones the issue goes away and all is well.  

I've had 14.04.3 installed before on the same system and never had this issue before.  I've also got dual boot with Windows 10, and it (Windows) does not have the same type of issue (glitching audio or phantom headphones)

My system is a Intel Core i7 4790K, 8GB 1600Mhz RAM, Gigabyte H97M-D3H motherboard with the latest BIOS version installed.  I've got an EVGA nVidia GeForce 750 Ti graphics card and internal graphics is disabled in BIOS setup.  It appears that this board has a Realtek ® ALC892 codec, if that makes a difference.  

Per the last thread there was some question of whether this occurs with the nVidia drivers or not.  It appears to occur regardless of the nVidia drivers being installed (proprietary or open source Nuveau).  

Any help would be appreciated.  

Thanks,
Ben.

---

### Post by nebhead772 on 2016-01-03
OK, so I found another helpful thread here that seems to be on the right track:  [http://ubuntuforums.org/showthread.php?t=2289737](http://ubuntuforums.org/showthread.php?t=2289737)

Unfortunately, there is still no permanent solution.  I followed the instructions to enter alsamixer and disable auto-mute.  The headphone jack still randomly pops up/gets detected in the sound settings dialog, however with auto-mute disabled it does not affect the audio playback.  This is definitely good progress, but would still like to see if we can push for a more robust solution here.  

Thanks,
Ben.

---

### Post by benjamin45 on 2016-01-03
I'm not sure there's really any way to 'properly' solve this -- it's simply a design flaw within the motherboard. Perhaps requesting that the folks working on alsa/pulse to add a feature similar to the Windows Realtek driver, where it has to detect the jack for a period of time before switching. But other than that, no 'permanent' solution other than simply purchasing a different sound card. The Creative Audigy Fx or SE (the latter of which does NOT include a front panel header!) are good, low-cost solutions as long as you don't plan on recording (the inputs have a noticeable amount of noise, but so does the motherboard audio anyway).

---

### Post by nebhead772 on 2016-01-03
> **benjamin45 said:**
> I'm not sure there's really any way to 'properly' solve this -- it's simply a design flaw within the motherboard. Perhaps requesting that the folks working on alsa/pulse to add a feature similar to the Windows Realtek driver, where it has to detect the jack for a period of time before switching. But other than that, no 'permanent' solution other than simply purchasing a different sound card. The Creative Audigy Fx or SE (the latter of which does NOT include a front panel header!) are good, low-cost solutions as long as you don't plan on recording (the inputs have a noticeable amount of noise, but so does the motherboard audio anyway).

Thanks for the tip!  I might just go pick up an Audigy FX so I can have the front panel support (amazon has the FX, used for $25)  I use the front panel headers all the time and it would be a shame to lose that functionality.  So I assume that these cards are fully supported in Ubuntu?

---

### Post by benjamin45 on 2016-01-05
> **nebhead772 said:**
> Thanks for the tip!  I might just go pick up an Audigy FX so I can have the front panel support (amazon has the FX, used for $25)  I use the front panel headers all the time and it would be a shame to lose that functionality.  So I assume that these cards are fully supported in Ubuntu?

The Audigy FX is. I have not tried the Audigy SE personally, but from what I can tell, it is supported as well.

Edit: I've looked up the Audigy FX and it seems some people have had bad experiences with it. IIRC my experience with it was fine. YMMV.

---

### Post by nebhead772 on 2016-01-05
> **benjamin45 said:**
> The Audigy FX is. I have not tried the Audigy SE personally, but from what I can tell, it is supported as well.

Edit: I've looked up the Audigy FX and it seems some people have had bad experiences with it. IIRC my experience with it was fine. YMMV.


Welp, my Audigy FX arrives in the mail tomorrow, so my fingers are crossed.  Hopefully since we had the same MB we'll have the same success.  :)

Installed the Audigy FX today and works great in Windows 10, however in Ubuntu 14.04.3, nothing but static the first time I booted.  Then upon reboot, no sound at all.  Bummer.  I started searching around for a fix and finally found a really simple fix thanks to the post here: [http://www.linuxquestions.org/questions/linux-hardware-18/getting-a-soundblaster-audigy-fx-to-work-4175505881/page2.html](http://www.linuxquestions.org/questions/linux-hardware-18/getting-a-soundblaster-audigy-fx-to-work-4175505881/page2.html) by Nortin on 3-6-2015.  Looks like the support was added in Alsa 1.0.29 (and I only had 1.0.27 installed).  

Beginning to wonder if the Alcatel 892 on the motherboard would also be fixed with this version.  Not that it matters now.  :)

---

### Post by benjamin45 on 2016-01-06
Nice to know you got it working!

---

