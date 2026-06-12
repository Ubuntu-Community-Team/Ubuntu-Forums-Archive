---
title: "Browsers FPS how to fix?"
date: 2024-05-10
forum: General Help
---

### Post by alextopic on 2024-05-10
Hello, I recently installed Ubuntu 24.04 LTS and I have a AMD 7800x3d and 7800xt graphics card.

I play this game Tanki Online and noticed the fps was different for a few browsers
I also did that online gpu stress test with bouncing ball sprites.

For Firefox I get 165 fps on my 165hz monitor and works good.
For Google Chrome, Vivaldi, Opera browsers I was getting 60fps.

I have 2 monitors 165Hz and 60Hz. When I just have 165Hz plugged in then Google Chrome gives me 165 fps, but
with the other monitor off/unplugged.

I tried Google Gemini and it suggested this at the google-chrome command line switch "--disable-gpu-compositing"  and another option
but couldn't find it for switches or chrome://flags "--force-refresh-rate".

When I used ---$ google-chrome-stable --disable-gpu-compositing
I get 100fps not 165fps; and my whole system runs hot compared to Firefox running cool and doing the 165fps.

I do have hardware acceleration enabled. I even went into BIOS to disabled the integrated GPU; I tried launch as dedicated Gpu.

Firefox works 100%, now what are they doing that is different than the rest?'
I am using Gnome version 46.
I usually use Google Chrome, but now use Firefox since it works, but this is bad for the other browsers and wonder why they default to 60Hz
as opposed to your highest fps.

If anyone has any idea, thanks I would love to know the problem.

---

