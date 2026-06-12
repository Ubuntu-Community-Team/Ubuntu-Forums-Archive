---
title: "Sound problems with flash."
date: 2006-09-23
forum: General Help
---

### Post by The Soundophiliac on 2006-09-23
The problems began after the update of the flash-plugin. I'm not getting any sound from flash-based videos like youtube or google video. Running firefox from terminal shows the following when playing videos:
```
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
Audio device open for 48Khz, stereo,16bit failed
Trying 22.05Khz, 8bit stereo.
Audio device open for 22.05Khz, stereo, 8bit failed
Trying 44.1Khz, 16bit mono.
Audio device open for 44.1Khz, mono, 8bit failed
Trying 22.05Khz, 8bit mono.
Audio device open for 22.05Khz, mono, 8bit failed
Trying 11.025Khz, 8bit stereo.
Audio device open for 11.025Khz, stereo, 8bit failed
Trying 11.025Khz, 8bit mono.
Audio device open for 11.025Khz, mono, 8bit failed
Trying 8.192Khz, 8bit mono.
Audio device open for 8.192Khz, mono, 8bit failed
Trying 8Khz, 8bit mono.
Sound device inadequate for Esound. Fatal.

```
That's the same I've been getting using gedit from the terminal. I've tried downgrading the flashplugin with no luck. Otherwise sound works fine. I've got an M-Audio Audiophile 2496.

I also tried the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=263333&highlight=sound+firefox](http://ubuntuforums.org/showthread.php?t=263333&highlight=sound+firefox)

Thanks

---

### Post by aysiu on 2006-09-23
Try [this](http://ubuntuforums.org/showthread.php?p=311733#post311733).

---

### Post by ogami1972 on 2006-09-26
Here's what i did:
1. remove libflash-mozplugin (i used synaptic- remember to right click and choose "complete removal" so as to remove any leftover config files!)

2.remove "flashplugin-nonfree"

3. reboot ( some steps maybe unecessary, but this is EXACTLY how i did it).

4 In synaptic , go 'settings>>properties' and select 'show package properties in main window'. apply. you should now see tabs 'description', 'common', 'dependencies', etc.

5. search or whatever to find and select 'flashplugin-nonfree'. go 'package>>force version...' and select the ".o63' version ( if you do not see an 0.63 version, let me know and i will send you my sources.list).

6. Install. Reboot ( again, probably unecessary)

7. In synaptic, search or whatever to find and select flashplugin-nonfree'.
 go 'package>>lock version'. Keep it locked and watch these forums until you hear '.068' flash is working.

8. Open firefox and enjoy the latest lonelygirl15 video!:D

---

### Post by The Soundophiliac on 2006-09-27
I fixed the problem. Don't remember how, though. I think I did something along those lines.

---

