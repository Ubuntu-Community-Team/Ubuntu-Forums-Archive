---
title: "mplayer, totem, xine: sound not syncronized"
date: 2005-04-18
forum: General Help
---

### Post by wetenschapper on 2005-04-18
hello,

with all 3 players the sound is not syncronized after 10 minutes

what can cause this problem?

---

### Post by fat_larry on 2005-04-18
I cannot offer more than to say that I also experienced sync issues, but running:

```
killall esd
``` 

solved the issue for me.  Maybe try this?  Someone more experienced will be able to offer you a more permanent solution

---

### Post by wolovids on 2005-04-18
I'm not sure if mplayer/xine use the Esound daemon by default.  Edit your ~/.mplayer/config file and make sure it has ```
ao=esd
``` Then edit the ~/.xine/config file and have esd set ```
# audio driver to use
# { auto  null  alsa  oss  esd }, default: 0
audio.driver:esd
```

I actually prefer the [Dmix setup](http://alsa.opensrc.org/index.php?page=DmixPlugin) that was suggested in [this](http://ubuntuforums.org/showpost.php?p=125432&postcount=12) post.  No more sound daemons for me!

---

