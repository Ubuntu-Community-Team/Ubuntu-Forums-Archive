---
title: "Help- Turn off auto mounting/ auto detection of removable media"
date: 2007-01-15
forum: General Help
---

### Post by nibsa1242 on 2007-01-15
I'm having a problem burning DVD-RW discs and regular CD-R (CD-RW and DVD+RW discs work fine). Many resources have informed me to turn off auto mounting of such discs and I did so by commenting the respective line in /etc/fstab . Yet even then if I insert a blank DVD-RW it still shows up on my desktop. sudo mount -l says that my DVD drive (hdc) is not mounted... what else do I need to do to burn successfully?

---

### Post by rainwalker on 2007-01-15
Try looking in System -> Preferences -> Removable Drives and Media. I think that might be what you're looking for (not sure though).

---

### Post by nibsa1242 on 2007-01-15
> **rainwalker said:**
> Try looking in System -> Preferences -> Removable Drives and Media. I think that might be what you're looking for (not sure though).

I've tried that. All that seems to do is edit /etc/fstab and even if I tell it not to automatically mount removable media it still shows up on my desktop...  strangely it doesn't seem to show up in mount -l . I suspect that whatever process is putting the icon on the desktop is disturbing my cd/dvd burning

---

### Post by rainwalker on 2007-01-15
Hm...well then I'm afraid I can't help you. Sorry :(

---

