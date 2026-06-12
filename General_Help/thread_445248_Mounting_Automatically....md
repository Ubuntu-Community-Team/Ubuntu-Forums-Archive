---
title: "Mounting Automatically..."
date: 2007-05-15
forum: General Help
---

### Post by amrclutch1 on 2007-05-15
When I boot up ubuntu automatically mounts /dev/hda1 and /dev/hda6, how can I make it not do this on reboot?

---

### Post by taurus on 2007-05-15
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and place a # in front of the lines for /dev/hda1 & /dev/hda6 to comment them out.  Save the changes and reboot.

---

### Post by amrclutch1 on 2007-05-15
Thanks! Fast response and it worked! This community is way better than the suseforums community imo :) I moved from suse because it is too user friendly, i like the idea of not being able to do something then later accomplishing it and feeling very good about myself. I am a gamer, and I am just going to remove my windows partition and wait until wine works with Call of Duty 2 1.3 with Punkbuster :grin:

---

### Post by taurus on 2007-05-15
If you are a gamer, then you should hang out in the Gaming & Leisure area.  That's where all the gamers are.

---

