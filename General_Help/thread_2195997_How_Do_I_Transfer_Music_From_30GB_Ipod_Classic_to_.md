---
title: "How Do I Transfer Music From 30GB Ipod Classic to 160GB Ipod Classic?"
date: 2013-12-27
forum: General Help
---

### Post by johnsmoke on 2013-12-27
For Christmas I just got a 160 GB ipod classic. I have a 30 GB ipod classic (thing is just about dead). Anyway, I wanted to see if there’s a way to transfer all the contents from my existing ipod onto the new one? I didn’t store my music in itunes – or in my case “Rhythmbox,” so they aren’t already in the player – didn’t do this in order to conserve HD space. Is there a way to do this in Ubuntu, with a program available on Ubuntu? If need be, I have a windows laptop I can use, but of course Ubuntu is my main OS & I’d like to stick with that if I am able to perform this task with it. Any info would be a great help. I’d hate to have to manually load all my music again from my cd’s!

---

### Post by johnsmoke on 2013-12-27
Never mind - I realized that when I originally imported my CD collection years ago, I did not change the import settings... so the default of 128k bit rate was used for all imported music. I want pretty much lossless quality... so I'm going to have to import everything again with the different import settings anyway to achieve this.

---

### Post by andrew.46 on 2013-12-27
I have one of the latest 160gig iPod classics and wrestled with the idea of import quality for a while before settling on alac. In theory I gather that this will give better playback when the iPod is hooked up to an external system / speakers. Great little device though I would feel better if its lossless format was flac...

---

### Post by FakeOutdoorsman on 2013-12-29
> **johnsmoke said:**
> so I'm going to have to import everything again with the different import settings anyway to achieve this.

If you're going to re-rip I recommend abcde which can utilize cdparanoia. You can rip to flac if you want lossless, and then use mp3fs to create a "virtual mirror" (mp3 files are encoded on the fly) using `lame -V 0` if you want to go overboard with the quality. Also see [Recommended LAME Encoding Settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_encoder_settings).

Makes me want to re-rip my 7 year old files...

---

