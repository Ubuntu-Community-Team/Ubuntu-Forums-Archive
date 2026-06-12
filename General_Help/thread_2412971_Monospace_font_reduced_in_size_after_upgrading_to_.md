---
title: "Monospace font reduced in size after upgrading to 14.04 LTS to 16.04 LTS"
date: 2019-02-19
forum: General Help
---

### Post by c_xy on 2019-02-19
Hello,

We recently upgrade from Ubuntu 14.04 LTS to Ubuntu 16.04 LTS server.

Upgrade went smooth. No functional problems. However, we did notice a reduction in font size for Monospace in the terminal window and System-wide font for shortcut labels, file menu words, etc.

I've attached two examples. Example 1 is 14.04 monospace font 10. Example 2 is 16.04 monospace font 10. Selecting monospace font 11 in 16.04 is much larger than the 14.04 Monopace 10 font. If we try 10.5 Monospace with 16.04 LTS it is somewhat bigger than the original size 10 in 14.04. 

This occurs whether we use LXDE as a desktop environment or Mate.

Is there a way to somehow revert back to the exact size of the 14.04 Monospace font within the new 16.04 LTS upgrade?

Why the change in fontsize between 14.04 and 16.04? We did not experience this phenomenon when upgrading from 10.04 to 14.04 several years ago.

Any input would be appreciated.

Thanks.

c

---

### Post by Impavidus on 2019-02-19
I have seen small changes in font rendering in the past, but I don't remember about the upgrade from 14.04 to 16.04 (which I actually did via the interim releases). It looks like the fonts stayed the same width, but have shrunken vertically by one pixel. Which means that the metrics of the font and the nominal size stayed the same, but the way the outlines of the characters are rounded to integer pixels changed. At small sizes a single pixel is quite noticeable. You could adjust size a bit, but I don't think you can make it render the fonts in exactly the same way as on 14.04.

---

### Post by c_xy on 2019-02-21
Thanks for your response.

When you say "adjust the size a bit", do you mean changing the font number (i.e., selecting 11 instead of 10 or 12 isntead of 10, etc.) or is there another way to adjust the size to make it similar to 14.04?


Thanks.

c

---

### Post by Impavidus on 2019-02-21
Yes, you could set it to 11 if 10 is too small.

The size hasn't actually changed since 14.04, but the characters are rendered slightly differently, making them appear smaller. Font rendering at small sizes is a bit of a special art. The outlines of the glyphs have to be modified to fit the edges of the pixels, whilst keeping the font's appearance regular, clear and close to the exact outlines. I assume the devs somehow decided that this is better.

---

