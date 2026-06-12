---
title: "Why are my keyboard shortcuts not working?"
date: 2013-02-02
forum: General Help
---

### Post by Lighosa on 2013-02-02
Setting>keyboard>shortcuts>sound and media
I then change the shortcuts for play/pause, previous track, and next track.
And then it works. Works perfectly. But if I log out in any way, it doesn't work the next time I log in. This is confusing me, anyone know what the deal is?

---

### Post by stinkeye on 2013-02-02
What keys are you using that get overridden.
Probably being used by compiz.

---

### Post by Lighosa on 2013-02-02
I'm using alt+end, alt+pageup, and alt+pagedown.
The really weird part is that each time I go back in, it still lists them, but they don't work.

---

### Post by stinkeye on 2013-02-02
> **Lighosa said:**
> I'm using alt+end, alt+pageup, and alt+pagedown.
The really weird part is that each time I go back in, it still lists them, but they don't work.

Yes I have same result.
Try using ctrl+alt or ctrl+shift

---

### Post by stinkeye on 2013-02-02
Just tested and you need to disable the alt key to "show the hud" and then alt+end etc works.
ccsm > desktop > ubuntu unity plugin.

May need to install ccsm
Terminal...
```
sudo apt-get install compizconfig-settings-manager
```

After install search in dash for ccsm.

---

### Post by Lighosa on 2013-02-02
Yep. That worked. Thank you very much

---

