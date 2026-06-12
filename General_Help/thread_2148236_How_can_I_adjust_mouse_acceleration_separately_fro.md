---
title: "How can I adjust mouse acceleration separately from sensitivity in 13.04?"
date: 2013-05-24
forum: General Help
---

### Post by vesayth on 2013-05-24
From what I have read, mouse acceleration and mouse sensitivity have been merged into 1 slider in 13.04. This is absolutely atrocious and makes no sense whatsoever. What's worse, is that every site reporting on this is touting this "feature" as one of the greatest things ever.

Anyways, I have managed to disable mouse acceleration using xinput, but I can't then adjust the sensitivity afterwards. The sensitivity property appears to not exist at all!

Obviously, this is a very frustrating issue to me. I would very much like to stay with 13.04 because of all of the performance improvements it has gotten. However, without being able to adjust my mouse to a comfortable setting, I will have to revert back to 12.10.

Does anyone have any ideas?

---

### Post by dino99 on 2013-05-24
two ways:
- with dconf (dconf-tools)
- via System Settings mouse

---

### Post by vesayth on 2013-05-24
System Settings Mouse does NOT work that way in 13.04. As I have stated (and has been mentioned in various articles), mouse acceleration and mouse sensitivity has been merged in that menu and they cannot be adjusted independently of one another.

I tried using dconf-editor to adjust it as you have suggested. However, there is no sensitivity property in there either. The only values are: double-click, drag-threshold, left-handed, locate-pointer, middle-button-enabled, motion-acceleration, motion-threshold.

Description for motion-acceleration: "Acceleration multiplier for mouse motion."
Description for motion-threshold: "Distance in pixels the pointer must move before accelerated mouse motion is activated."

As you can see, both only affect acceleration and not sensitivity.

---

### Post by vesayth on 2013-05-27
bump

---

