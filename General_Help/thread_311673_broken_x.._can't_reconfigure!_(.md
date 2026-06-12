---
title: "broken x.. can't reconfigure! :("
date: 2006-12-03
forum: General Help
---

### Post by a.d.gardiner on 2006-12-03
hey all,

i just ran easyubuntu to install some fonts that i needed. i got tempted and clicked to install the official nvidia graphics drivers.

only thing is now xorg is broken.

i have tryed sudo dpkg-reconfigure xserver-xorg but that doesnt seem to fix things.

i tried to go back to the original version of my driver with apt-get install nvidia-glx-legacy but apt reports broken dependencies.

anybody? im really stuck because i broke my work machine!](*,)

---

### Post by noneofthem on 2006-12-03
Hey!

Run sudo dpkg-reconfigure xorg-server again and select "vesa" as the driver. If that doesn't fix it also try to select a lower resolution for your monitor.

I hope that helps.

Amir

---

### Post by a.d.gardiner on 2006-12-03
:) straight in, many thanks!

turns out i have some kind of broken package so I can't reinstall nvidia-glx-legacy. just got to work out how to fix it.

---

### Post by noneofthem on 2006-12-03
No problem! Had the same problem many times. Especially when learning how to install the ATI driver...

Feel free to ask again. This is why we are all here...

---

### Post by a.d.gardiner on 2006-12-03
:) cheers man.

---

