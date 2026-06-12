---
title: "Help with wifi driver problem"
date: 2006-07-12
forum: General Help
---

### Post by shawnrgr on 2006-07-12
After some researching i figured out that this driver was for my broadcom wifi driver (which I don't use) but here is the error im getting at boot:

```

firmware_helper[3278]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw for
divice '/class/firmware/0000:02:02.0' with driver 'bcm43xx'
[17179588.152000] bsm43xx: Error: Microcode "bcm43xx_microcode.fw" not available or load failed.

firmware_helper[3278]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw for
divice '/class/firmware/0000:02:02.0' with driver 'bcm43xx'
[17179588.160000] bsm43xx: Error: Microcode "bcm43xx_microcode.fw" not available or load failed.

```

maybe in the future i would want to use my wifi but i don't even have my wifi router out anymore. If its possible, can we just have the system not load drivers for the device? and skip it all togeather? i don't know... what the best option, fix it in case i need it someday?

Any help on this would be great... thank you!

---

### Post by DarkOx on 2006-07-12
Open up a terminal, and type

> sudo gedit /etc/modprobe.d/blacklist

add "blacklist bcm43xx" to the end of the file that loads, save and exit. The driver won't load anymore.

---

### Post by shawnrgr on 2006-07-13
ahhh that did the trick! thanks ;) this way if i ever wanna use my wifi again, i can just take it off the list and then try to fix the error. for now all is good. Thanks!

---

### Post by pybuntu on 2006-07-16
Hi all,
I`ve the same problem but I should fix this can anyone tell me how to ?

---

