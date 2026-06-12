---
title: "Burn music CD with normalized audio woes"
date: 2007-04-26
forum: General Help
---

### Post by BLTicklemonster on 2007-04-26
I have some audio files of varying audio levels that I would like to burn to an audio cd. I tried using k3b, but the normalize function does not work. Some bug with k3b not looking for the right name when it looks for normalize-audio. Can k3b be made to use normalize, and if so, how, or is there another cd burning program that can perform this function?


Running Feisty, btw.

---

### Post by DoktorSeven on 2007-04-26
See [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/44524](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/44524)

And symlinking normalize-audio to normalize doesn't work.  Just wait till they iron out that bug, I guess; I really don't use any other CD burners except commandline.

You can use normalize-audio manually then use k3b to burn the files.  Hard way, but it'd work.

---

### Post by BLTicklemonster on 2007-04-26
Thanks, I saw that bug, I was just hoping someone could explain what they mean by symlink. Well, okay, not explain what, but explain how. :)

---

