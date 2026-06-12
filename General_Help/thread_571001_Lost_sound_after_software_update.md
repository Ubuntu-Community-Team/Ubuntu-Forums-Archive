---
title: "Lost sound after software update"
date: 2007-10-08
forum: General Help
---

### Post by Marty McFly on 2007-10-08
After a recent software update, my sound was lost on my computer.  I'm running 7.04 and it's not a system76 computer.

I tried the alsamixer PCM boost mentioned here:  [http://ubuntuforums.org/showthread.php?t=380800](http://ubuntuforums.org/showthread.php?t=380800) but that didn't work either.

Any help/ideas would be appreciated.

---

### Post by tankertuff on 2007-10-09
have you made sure any secondary sound, or onboard sound is disabled, I know I've bashed my head in over that before. other than that, I have no idea.

---

### Post by Marty McFly on 2007-10-09
I don't have any onboard sound, just by soundblaster card.

---

### Post by Joeb454 on 2007-10-09
Is the sound lost altogether?

I.e. can you play music from rythmbox / amarok etc.

Or is it just when you boot up the computer - the log on sounds don't play

---

### Post by Marty McFly on 2007-10-09
None of the above, no login music, no music from websites, nothing works....but when I boot into Windows it's fine and it worked in Ubuntu before I did this recent update.

---

### Post by gmjs on 2007-10-09
Yep - same happened to me.  I recommend downloading and installing the lastest ALSA drivers - it worked for me:

[http://ubuntuforums.org/showthread.php?t=551697]("http://ubuntuforums.org/showthread.php?t=551697")

Graham

---

### Post by Marty McFly on 2007-10-15
I have read up on the alsa thing and I am totally lost without a step-by-step command line list of instructions.

Also how do I know that it will work for my soundcard?  I have a sound blaster live.

Any other ideas?

---

### Post by Marty McFly on 2007-10-16
Mid-day bump^

---

### Post by AggieBob on 2007-12-21
I don't know if you're still having trouble with the sound, but I recently had a similar issue with my Toshiba Satellite notebook running Ubuntu Feisty Fawn.  I don't know if this will work for you, but the key to restoring sound on my laptop was to re-compile the alsa drivers, alsa lib, and alsa -utils using the most recent versions from the ALSA project site.  Follow the Howto from this Ubuntu community document,
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
Re-compiling with any other version of ALSA gave me errors.  The versions I used were,
alsa-driver-1.0.15rc3, alsa-lib-1.0.15rc3, and alsa-utils 1.0.15rc1.  Make sure to modify the directory with the version of ALSA you're using.

Cheers,

Bob

---

