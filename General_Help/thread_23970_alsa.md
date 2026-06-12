---
title: "alsa?"
date: 2005-04-04
forum: General Help
---

### Post by deucedlt on 2005-04-04
Is there an easy way to get alsa working? My new install of warty does not seem
to have the alsaconf command. Synaptic shows only alsa-base and alsa-utils
installed. Repository search shows some other alsa packages but not for kernel
2.6.8.1-3. I have an als100 sound card which I have been able to S.U with alsa
on other distros using the alsaconf command.

---

### Post by deucedlt on 2005-04-05
I get it!! "alsa" must be a dirty word in some African language lol. Seriously does
anyone know an alernative for simple soundcard setup?

---

### Post by Svictor on 2005-04-05
As far as I know, there is no "simple" way to set up alsa with ubuntu. Alsaconf seems not to exist in the ubuntu version of alsa-utils. However, there were a few threads already on that topic which might be of help. See this one in particular (pretty long but it got me out of trouble) : [http://www.ubuntuforums.org/showthread.php?t=8882&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=8882&page=1&pp=10)
Note however that for this to work, you should upgrade to Hoary (which will be officially released in 5 days so you don't risk much). In Hoary, the things to tweak should be "Enable soundserver on startup" (in System --> Preferences --> Sound) and the "Multimedia Systems Selector" (in System menu).
I can't tell you much more since I'm far from understanding everything. I hope all this is not too obvious for you. Try to see that thread, maybe it will help.

---

### Post by deucedlt on 2005-04-05
Thanks for the input Svictor. It told me stuff I wanted to know.

---

