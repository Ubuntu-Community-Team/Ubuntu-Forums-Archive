---
title: "GTK3 check boxes: I don't understand the css :("
date: 2016-02-01
forum: General Help
---

### Post by vasa1 on 2016-02-01
The Numix theme which comes as part of the shimmer-themes packages (in the software center) has this file: /usr/share/themes/Numix/gtk-3.0/gtk-widgets-assets.css

I don't understand the following code:
```
/*******************
 * check and radio *
 *******************/

.check,
.check row:selected,
.check row:selected:focus {
    background-image: linear-gradient(to bottom, @theme_base_color, @theme_base_color),
                      linear-gradient(to bottom, @theme_base_color, @theme_base_color),
                      linear-gradient(to bottom, shade(@theme_base_color, 0.6), shade(@theme_base_color, 0.6)),
                      linear-gradient(to bottom, shade(@theme_base_color, 0.6), shade(@theme_base_color, 0.6)),
                      -gtk-gradient(radial, center center, 0, center center, 0.5, to(@theme_base_color), to(transparent)),
                      -gtk-gradient(radial, center center, 0, center center, 0.5, to(@theme_base_color), to(transparent)),
                      -gtk-gradient(radial, center center, 0, center center, 0.5, to(@theme_base_color), to(transparent)),
                      -gtk-gradient(radial, center center, 0, center center, 0.5, to(@theme_base_color), to(transparent)),
                      -gtk-gradient(radial, center center, 0, center center, 0.5, to(shade(@theme_base_color, 0.6)), to(transparent)),
                      -gtk-gradient(radial, center center, 0, center center, 0.5, to(shade(@theme_base_color, 0.6)), to(transparent)),
                      -gtk-gradient(radial, center center, 0, center center, 0.5, to(shade(@theme_base_color, 0.6)), to(transparent)),
                      -gtk-gradient(radial, center center, 0, center center, 0.5, to(shade(@theme_base_color, 0.6)), to(transparent));

    background-position: center center, center center, center center, center center, 6% 6%, 6% 94%, 94% 94%, 94% 6%, 0% 0%, 0% 100%, 100% 100%, 100% 0%;
    background-size: 80% 90%, 90% 80%, 80% 100%, 100% 80%, 10% 10%, 10% 10%, 10% 10%, 10% 10%, 20% 20%, 20% 20%, 20% 20%, 20% 20%;
    background-repeat: no-repeat;
}

```For a start, why do lines repeat for "background-image", twice in some cases, four times in others?

**Edit: **
I sort of figured out why. The clue is that each line has a pair of figures in *background-position* and *background-size* thus making them distinct from each other.

---

