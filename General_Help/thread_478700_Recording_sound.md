---
title: "Recording sound"
date: 2007-06-19
forum: General Help
---

### Post by Silenus on 2007-06-19
Whenever I try to record sound from my microphone using sound recorder it captures nothing, and I can't find a fix for it, is there anyone who has an idea to why, I can hear the sound, but it doesn't capture it.

---

### Post by Crafty Kisses on 2007-06-19
> **Silenus said:**
> Whenever I try to record sound from my microphone using sound recorder it captures nothing, and I can't find a fix for it, is there anyone who has an idea to why, I can hear the sound, but it doesn't capture it.

Try using "Audacity"
```
sudo apt-get install audacity
```

---

### Post by Silenus on 2007-06-19
How do I configure it for the microphone

---

### Post by Silenus on 2007-06-19
I am trying to use the ekiga service aswell and my friend can not hear the mic through it, I am unsure of what the problem is, but it projects through the speakers fine.

---

### Post by Keisad on 2007-06-21
Something you might be able to do is to turn up the "capture" or the "in gain" through the volume control panel. 

With the way your describing things, it seems like the "microphone" setting is adjusted properly, but you may need to adjust the in gain or capture setting in order for your computer to record from your microphone, or for your friend to be able to hear it as well.

In addition, make sure you have the correct microphone selected. Repost if your unsure how to do these things.

---

### Post by energiya on 2007-06-21
I had the same problem, and the fix was to play with the mic/gain settings in alsamixer and aumix.

---

