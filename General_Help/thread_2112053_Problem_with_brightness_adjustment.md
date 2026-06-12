---
title: "Problem with brightness adjustment"
date: 2013-02-03
forum: General Help
---

### Post by fleneh on 2013-02-03
Hi. I have a Sony Vaio VPCY2 laptop with Ubuntu 12.04 64 bits. I can't modify the brightness of the screen with the keyboard (Fn+F5/F6) neither from General Settings-Brightness (when I move the brightness adjustment bar it does nothing).
Thanks!

---

### Post by fleneh on 2013-02-04
When I enter ```
echo 2000| sudo tee /sys/class/backlight/intel_backlight/brightness
``` in terminal it reduces brightness ~50% (I think 4000 is maximum). 
Is it possible to change brightness using keyboards commands like Fn+F5/F6?
Thanks

---

### Post by fleneh on 2013-02-06
I followed this post and it worked :) [http://ubuntuforums.org/showthread.php?t=2086359](http://ubuntuforums.org/showthread.php?t=2086359)

---

