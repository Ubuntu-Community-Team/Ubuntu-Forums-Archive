---
title: "Why svg instead of png file for icons?"
date: 2019-03-21
forum: General Help
---

### Post by raleigh3 on 2019-03-21
I noticed that a lot of icons are .svg.

Is there an advantage to png?

The sizes are similar.

---

### Post by freemedia2018 on 2019-03-21
As a raster format, png doesn't scale as nicely.

---

### Post by raleigh3 on 2019-03-21
What does scale mean?

Does it refer to the ability to resize an icon?

---

### Post by CatKiller on 2019-03-22
> **raleigh3 said:**
> What does scale mean?

Does it refer to the ability to resize an icon?

Yes. SVGs (scalable vector graphics) are actually text files. The images they describe can be rendered at any resolution cleanly. PNGs are raster graphics: they have a fixed resolution, like bitmaps, and will be blurry or distorted if displayed at a different resolution.

In principle, you could have a single SVG instead of multiple PNGs for each size, and simply scale that to the size you want, although, in practice, simplified versions are used at smaller sizes for clarity.

---

