---
title: "Screen brightness bug; adjusts gain, not brightness :("
date: 2019-02-22
forum: General Help
---

### Post by ProDigit on 2019-02-22
Running Lubuntu off of an HP Stream 11 netbook.
In the brightness section found in Configuration Center, I can clearly see that my brightness keys (F2/F3) are assigned to gain, not actual brightness.
This makes the screen look washed out.
Increasing brightness makes everything look too bright; colors are off.
Decreasing brightness makes everything look grey.

When I center gain, and manually set brightness via the slider in the Brightness section, the screen backlight goes darker, and colors still stay relatively natural.
But when I adjust the gain rotary dial, the colors of photos look off.

I think this is a bug.

How can I reassign the screen brightness keys to set brightness, rather than gain?
I know I can just type:
```
echo 750 | sudo tee /sys/class/backlight/intel_backlight/brightness 
```
But I prefer to have them set to the keys.

---

