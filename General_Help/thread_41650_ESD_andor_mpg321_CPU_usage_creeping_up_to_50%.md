---
title: "ESD and/or mpg321: CPU usage creeping up to 50%"
date: 2005-06-14
forum: General Help
---

### Post by tristan on 2005-06-14
Hi all

I'm using mpg321 to randomly play mp3 files in the backgound of gnome or xfce. What I notice is that after a few minutes of playing songs, my CPU usage creeps up to 50%. A quick look at top shows esd is responsible for the usage. If I kill either mpg321 or esd, the processor usage drops. If I start mpg321 again (which will autospawn esd), sooner or later the usage goes up again. 

If I don't use mpg321, esd sits there happily enough not using any cpu time.

This isn't a life threatening thing, but I wonder if anyone has any ideas anyway!

---

