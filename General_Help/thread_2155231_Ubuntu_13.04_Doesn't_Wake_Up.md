---
title: "Ubuntu 13.04 Doesn't Wake Up"
date: 2013-06-17
forum: General Help
---

### Post by stokedboss on 2013-06-17
I just installed 13.04 on my machine, and when I suspend it, everything is fine until you "wake" it up. It loads my wallpaper, and that's it I can see the mouse and move it, but just a wall paper nothing else. Any ideas?

---

### Post by sgage on 2013-06-17
> **stokedboss said:**
> I just installed 13.04 on my machine, and when I suspend it, everything is fine until you "wake" it up. It loads my wallpaper, and that's it I can see the mouse and move it, but just a wall paper nothing else. Any ideas?

Do you have an nvidia graphics card? I do, and resume from suspend doesn't work for me unless I use the proprietary nvidia drivers. I think nouveau will work fine for some nvidia cards - it's just certain models. (I have a GeForce 8500 GT)

---

### Post by stokedboss on 2013-06-17
Yes I have an nvidia 460GTX. I installed the drivers and it works again! Thanks so much.

---

### Post by sgage on 2013-06-18
> **stokedboss said:**
> Yes I have an nvidia 460GTX. I installed the drivers and it works again! Thanks so much.

Great! Resume-from-suspend worked (for my card) using the free nouveau driver under Precise, but as of Raring, no go. Doesn't work in Saucy, either. Oh well.

---

