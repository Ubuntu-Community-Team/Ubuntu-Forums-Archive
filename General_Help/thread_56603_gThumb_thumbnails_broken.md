---
title: "gThumb thumbnails broken"
date: 2005-08-13
forum: General Help
---

### Post by mättä on 2005-08-13
For some reason, gthumb doesn't show any thumbnails anymore. The images can be viewed and edited one by one but the thumbnail page just shows boring empty icons.

Nautilus and F-Spot both have no problems with thumbnails. Deleting ~/.thumbnails doesn't help anything.

Any clues?

---

### Post by MeneM on 2005-08-30
Hi all,

I have the exact same problem! I too am unable to view the thumbnails! What can we do?

Nautilus, and other programs have no problem with the thumbnails/previews.

Thanks,
Mark

---

### Post by MeneM on 2005-08-30
Hi all,

I just found out that if you log into as a new user, gthumb works perfectly.

So I tried deleting all directory's and file's called gthumb in my home directory. but still a no show...?

Mark

---

### Post by MeneM on 2005-08-30
I've got it!

Goto Applications -> System tools -> configuration editor.

Then:
/apps/gthumb/browser and turn "show_thumbnails" back on.

Hope it helps.

---

### Post by mättä on 2005-09-28
That solved it for me. Thank you for the tip!
Just wondering why this entry was off...
Greets

---

