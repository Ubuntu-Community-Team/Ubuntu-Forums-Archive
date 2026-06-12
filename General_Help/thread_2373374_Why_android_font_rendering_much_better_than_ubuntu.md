---
title: "Why android font rendering much better than ubuntu?"
date: 2017-10-05
forum: General Help
---

### Post by widon1104 on 2017-10-05
I use the same font used in android cellphone to ubuntu.
The font rendering effect is perfect in android, but terrible in ubuntu.

---

### Post by ian-weisser on 2017-10-05
The fonts I use in Ubuntu render beautifully.
I wonder what you are doing differently?

---

### Post by widon1104 on 2017-10-05
The font I use is chinese character vector font.

---

### Post by Bucky Ball on 2017-10-06
> **widon1104 said:**
> The font rendering effect is perfect in android, but terrible in ubuntu.

Did you want support with this or just thought you'd mention it? If the former, best post a support thread in a support area or report your first post and ask staff to move the thread as this is a chat area, not a support one. ;) 

Good luck.

---

### Post by widon1104 on 2017-10-06
Of course I want ubuntu increase the font rendering effect when use vector font.

---

### Post by slickymaster on 2017-10-06
Thread moved to **General Help** for a better fit

---

### Post by Impavidus on 2017-10-06
High quality font rendering on raster displays depends on font hinting, which helps to align features of the glyphs with pixels on the screen. Hinting may be built-in into the font, but many renderers can do their own hinting. For latin or cyrillic characters this is much easier than for chinese. My guess is that android uses some proprietary algorithm for hinting of chinese characters that's not available on Linux.

Using a different font might help, one with high quality hinting built-in or even a raster font.

---

