---
title: "java sound api cannot be loaded? (tuxguitar)"
date: 2008-05-22
forum: General Help
---

### Post by treehouse on 2008-05-22
I get an alert that says, "java sound api cannot be loaded" when I open up Tuxguitar. This of course means I don't get playback :(

I have no clue what to do.

---

### Post by xtremethegreat1 on 2009-03-04
Try installing timidity:
> sudo apt-get install timidity
Then in tuxguitar, just go to settings and set the audio to timidity.
I'm facing this same problem. I'm installing timidity right now. If it works for me, I'd post it here. If you try it before I do, post if it worked.

---

### Post by xtremethegreat1 on 2009-03-05
I'm assuming that you're using the program after getting from the main website rather than the Ubuntu repository. Okay timidity doesn't work. You'd have to install libtritonus-java and libtritonus-bin and Sun Java version sun-java6-bin from Synaptic Package Manager or type the following in a command line:

```
sudo apt-get install libtritonus-java sun-java6-bin
```

This worked for me. Also, after you're done, you can optionally add some soundbank from the Java Sound API and install them as instructed in the readme file that comes alongwith. Remember that since we're using Ubuntu, the <install-dir> would be /usr/lib/jvm/java-6-sun/.

I hope it works for you as well.

;)

---

