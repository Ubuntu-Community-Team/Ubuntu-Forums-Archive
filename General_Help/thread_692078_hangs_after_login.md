---
title: "hangs after login"
date: 2008-02-09
forum: General Help
---

### Post by davbren on 2008-02-09
Hey I was just copying some fonts over. The nautilus window "forced quit" i restart and I haven't been able to see anything on my desktop (except mouse and wallpaper) since.

Any ideas?

Ok It turns out it was the fonts being stupid so I went into the failsafe terminal and typed:

sudo mv '/home/dave/.fonts' '/home/dave/.fonts2'

this let my account just use the root's fonts, worked a treat.

---

### Post by davbren on 2008-02-09
sorry to bump but i really need my pc :S

---

