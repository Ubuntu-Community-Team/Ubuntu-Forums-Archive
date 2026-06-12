---
title: "Mime Type association gone"
date: 2007-08-24
forum: General Help
---

### Post by Modius on 2007-08-24
After following instructions in the post [http://ubuntuforums.org/showthread.php?t=423883&highlight=gdesklets&page=2](http://ubuntuforums.org/showthread.php?t=423883&highlight=gdesklets&page=2)
 and got my gDesklet working, the MIME Types for ALL my files got changed to application/octet-stream and all the files icons are gone.:( I can't seem to find anything relating to this in the board, Is there a way to restore the settings?

---

### Post by capink on 2007-08-24
I'm not so sure that would help. Try typing:

```
sudo update-mime-database
sudo update-desktop-database
```

---

### Post by Modius on 2007-08-24
> **capink said:**
> I'm not so sure that would help. Try typing:

```
sudo update-mime-database
sudo update-desktop-database
```

Tried it.Didn't seems to work for my situration. 
I also found out that Konqueror dosen't seems to be affected, totally normal. It's just gnome that is messed up. 
So another question, is it possible that I can port those MIME settings in Konqueror and use it in Gnome? I'm really a newibe in this, thx in advance.

---

### Post by capink on 2007-08-24
Have you tried the solution posted [here]("http://ubuntuforums.org/showthread.php?p=2953931").

---

### Post by Modius on 2007-08-24
Ah..:KS That worked perfectly fine, thank you.
Stupid me, should've search for "File Association" instead of "MIME".:lolflag:

---

