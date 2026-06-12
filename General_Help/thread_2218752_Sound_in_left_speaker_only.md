---
title: "Sound in left speaker only"
date: 2014-04-21
forum: General Help
---

### Post by agemini68 on 2014-04-21
I upgraded to 14.04. After several unsuccessful attempts to get my built in audio to work, I gave up and bought a brand new Soundblaster Audigy SE sound card and now I only have sound in the left speaker. I have tried some fixes, but nothing worked so far, any solutions? Yes I checked the mute and balance settings. I'm not completely new to this, but not sure of terminal commands.

---

### Post by agemini68 on 2014-04-23
#-o#-o#-oI have the fix, My mouse would work to raise the bars up, but wouldn't select the other bars, didn't think to try the arrow keys. 
1. launch alsamixer (from console).
2. Select your soundcard (press F6), mine was CA0106.
3. Look for stereo items with one channel muted (text beneath bars looks like "63<>0").
4. Make volumes equal (63<>63) using keyboard controls (UP/DOWN, Q/Z, E/C).
5. Exit (ESC), no need to save manually.

---

### Post by don20 on 2014-05-23
Thanks for the tip, it made my day. In my new install of Ubuntu Studio 14.04 LTS, I had to enable "view: all" (F5) in order to gain control and make the appropriate adjustments. Just adjusting in "Playback" (F3) gave me no joy on the right channel.

---

