---
title: "[SOLVED] No sound output on Acer Aspire"
date: 2008-02-13
forum: General Help
---

### Post by littletinman on 2008-02-13
Here's my problem. I've tryed absolutely everything to get sound on my acer aspire 5520. So far i've gotten it to recognize and use the sound card. the only problem is there is no output from the speakers or the headphones. I'm pretty sure nothing is muted but if you could tell me EXACTLY how to tell that would be great. This is frustrating because i know other people have ahd success but i'm not getting it. I've tryed everything i could. Sound worked perfectly in Vista before i switched over.  I NEEED help!!!!

---

### Post by scottfree on 2008-02-13
I have an Aspire 5920, which is probably similar.  I had to go into the preferences for the sound icon and tell it to use "surround".  I still can't get the volume wheel on the front of my laptop to control the volume, but at least I can control it using the speaker icon.

---

### Post by littletinman on 2008-02-14
there's no surround option. just master, pcm and digital.

---

### Post by kesman on 2008-02-14
check out alsamixer in terminal and be sure to select "all" channels with TAB-key. If a channel is muted, there's MM or M below the channel bar. Hit M to unmute a channel.

---

### Post by littletinman on 2008-02-14
I'll try that when i get beck from my math class. I'll let you know what happens. Others have reported the problem is fixed in Hardy Haron 8.04 so i might give that a shot.

---

### Post by Kilz on 2008-02-14
> **littletinman said:**
> there's no surround option. just master, pcm and digital.

The master pcm and digital are on the volume control, make sure none have a Xed out speaker below them. While you are in that window, click Edit, then Preferences, check the surround sound option. Then make sure its checked on the switches tab.

---

### Post by littletinman on 2008-02-14
there are no switches tab and the only choices are master, pcm, and digital. Nothing else is there to select.

---

### Post by Kilz on 2008-02-14
> **littletinman said:**
> there are no switches tab and the only choices are master, pcm, and digital. Nothing else is there to select.

Do you see a row of words at the top of that that says File Edit and Help ? if not take a screen shot with the volume control showing and attach it to a post here. You can find the screen shot at Applications > Accessories > Take Screenshot

---

