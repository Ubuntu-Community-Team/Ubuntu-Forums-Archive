---
title: "Alarm?"
date: 2008-05-30
forum: General Help
---

### Post by Cringle on 2008-05-30
Hey all, I am a fairly new Linux/ubuntu User and am struggling to find the best workaround for an alarm at a specific time to play a music file.

I am currently using the 'alarm' plugin for Rhythmbox. But as I also use my laptop for listening to music as I sleep, at some point I need the volume to increase.

Any Ideas?

Thanks alot, 
Chris

---

### Post by HalPomeranz on 2008-05-30
You could write a script that uses "aplay" to play a sound file, and then trigger that script at a specific time via cron.  If you're not familiar with cron, there's a quick intro in one of my posts in another thread: [http://ubuntuforums.org/showpost.php?p=5075568&postcount=2](http://ubuntuforums.org/showpost.php?p=5075568&postcount=2)

---

