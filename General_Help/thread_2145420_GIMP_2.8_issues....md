---
title: "GIMP 2.8 issues..."
date: 2013-05-15
forum: General Help
---

### Post by Jason Kuzhively on 2013-05-15
I have a couple of problems with using GIMP 2.8. When I scale an image to a smaller size, the quality is reduced to s**t! and I don't have the horizontal scrolling bar.

---

### Post by raja.genupula on 2013-05-15
> **Jason Kuzhively said:**
> I have a couple of problems with using GIMP 2.8. When I scale an image to a smaller size, the quality is reduced to s**t! and I don't have the horizontal scrolling bar.


you are saying that to smaller size , as it says if you set the picture to proper resolution then it will have the quality . If you change it you will lose the quality of the image . 

for horizontal scrolling bar you may check in preferences.

---

### Post by timgood on 2013-05-15
I'm having some trouble understanding your problem. When you scale an image to a smaller size, you decrease the number of pixels in the image. Therefore the quality is bound to be reduced. You can view the image full size by changing the % at the bottom of the screen, under the picture. If you make the picture smaller than the window, you will not be able to scroll horizontally or vertically.

Hope this helps.

---

### Post by Jason Kuzhively on 2013-05-15
So wait, the quality of the image is reduced when you reduce it's size? I though that only happens if you increase it and BTW, I'm running GIMP in Single-Window mode.

---

### Post by ajgreeny on 2013-05-15
> **Jason Kuzhively said:**
> So wait, the quality of the image is reduced when you reduce it's size? I though that only happens if you increase it and BTW, I'm running GIMP in Single-Window mode.
No, of course it doesn't!

If you reduce an image that was 2000x1000pixels to a scaled size of 200x100 pixels, you now have an image with 20,000 pixels instead of the original with 2,000,000 pixels.  There is no way to avoid this as far as I'm aware.

Perhaps you misunderstood the term "scale"?

Single window mode has no bearing on your situation, so don't worry about that!

---

### Post by Jason Kuzhively on 2013-05-15
> **ajgreeny said:**
> No, of course it doesn't!

If you reduce an image that was 2000x1000pixels to a scaled size of 200x100 pixels, you now have an image with 20,000 pixels instead of the original with 2,000,000 pixels.  There is no way to avoid this as far as I'm aware.

Perhaps you misunderstood the term "scale"?

Single window mode has no bearing on your situation, so don't worry about that!

Thank you, one more thing, my horizontal scrollbar is nowhere to be seen.

Update: When I use it in multi-window, I can see the horizontal bar, and the vertical scroll bar is pushed out a bit.

---

### Post by Jason Kuzhively on 2013-05-16
Fixed it, I just went to ~/.gimp-2.8 folder and deleted the sessionrc file.

---

