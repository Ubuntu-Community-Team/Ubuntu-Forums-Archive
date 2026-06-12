---
title: "flashplugin-installer update problem"
date: 2015-01-26
forum: General Help
---

### Post by Extreedoc on 2015-01-26
Running Ubuntu 14.04 LTS 64 bit. Keep getting message: "Failure to download extra data files.  Flashplugin - installer

Software updater just tried to download a lot of stuff Flashplugin installer related today and stalled part-way through.

Any good ideas?

[ATTACH=CONFIG]259505[/ATTACH][ATTACH=CONFIG]259506[/ATTACH]

---

### Post by slickymaster on 2015-01-26
Try this:```
sudo apt-get remove --purge flashplugin-installer
sudo apt-get install flashplugin-installer
```

---

### Post by echotech2 on 2015-01-26
FWIW, todays update of flash via Software Updater hung for about 10 minutes halfway through.  I just left it running and it finally completed.

---

### Post by mörgæs on 2015-01-26
Did you notice the footnote in the post above you?

---

### Post by Extreedoc on 2015-01-26
Well, I tried re-installing flashplugin-installer and still got the "Failure to download extra... etc". I'll give it a day or so and see if I still keep getting warnings.

---

### Post by Extreedoc on 2015-01-26
> **mörgæs said:**
> Did you notice the footnote in the post above you?

Sorry, I don't understand this at all, what point are you making please?

---

### Post by Extreedoc on 2015-02-03
Not sure what happened but after re-installing flashplugin-installer and a few more warnings it seems to have fixed itself, maybe it was at last able to download the required extra data files? Anyway, thanks to those who offered help.

---

