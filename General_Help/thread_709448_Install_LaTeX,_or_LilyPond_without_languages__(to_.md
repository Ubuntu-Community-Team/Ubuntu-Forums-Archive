---
title: "Install LaTeX, or LilyPond without languages  (to save disk space)"
date: 2008-02-27
forum: General Help
---

### Post by nmsmith on 2008-02-27
I just tried ```
sudo aptitude install lyx
``` and got ```
Need to get 343MB of archives. After unpacking 718MB will be used.
```
This is not great, as I have a 10GB root partition with only 1.5GB currently free. Most of the packages are things like texlive-lang-german which I don't really need.
Is there a way to install LyX, LaTeX, or LilyPond with a smaller footprint?

---

### Post by mikewhatever on 2008-02-27
Try using apt-get instead of aptitude. It would still require quite a lot of space, but you should not get the recommended packages, just the dependencies.

---

