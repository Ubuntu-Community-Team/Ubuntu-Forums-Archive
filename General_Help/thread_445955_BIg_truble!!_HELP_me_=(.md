---
title: "BIg truble!! HELP me =("
date: 2007-05-16
forum: General Help
---

### Post by semka on 2007-05-16
[IMG]http://t.foto.radikal.ru/0705/28/0232ec5ec71a.jpg[/IMG]


Help me please, problem with **Midnight commander**...(ubuntu server 6.06 LTS)

---

### Post by irw on 2007-05-16
If you want help, then you need to give us more detail - what actually is your problem?

---

### Post by asipi on 2007-05-17
tipically character encoding problems with mc... I also had similar through ssh, try to set your locale to english mc should have work well.

mc is a good tool, but not perfect and let say it is old :(

---

### Post by semka on 2007-05-17
**asipi**  please more info?!

YES i need to change coding FR to EN, how i can?

---

### Post by asipi on 2007-05-17
e.g for temporary try to give the environmental variable in a terminal:
LANG=en_US
and then start mc and let see what happen. keep in mind that this is valid for only that terminal session, if you exit, the others will get the system default

---

### Post by semka on 2007-05-17
> **asipi said:**
> e.g for temporary try to give the environmental variable in a terminal:
LANG=en_US
and then start mc and let see what happen. keep in mind that this is valid for only that terminal session, if you exit, the others will get the system default

where??? /root/ ??? or ? in what file i can change?

---

### Post by semka on 2007-05-17
> **asipi said:**
> e.g for temporary try to give the environmental variable in a terminal:
LANG=en_US
and then start mc and let see what happen. keep in mind that this is valid for only that terminal session, if you exit, the others will get the system default

Waaaaaaaaoooowwwww!!!!!!!!!!!!!!!! Thanks!!!!!!!!!!!!!!!!!! its wooork!!!!!!! 



BIG BIG BIG THANKS! And when i exit , and reconnect in mc its again not correctly disply

---

### Post by asipi on 2007-05-17
I guess you want to keep your native locale for the applications so that's why I told ya set it temporary only for the session you want to use with mc.

You can write a small shellscript to do it for you and then make a launcher icon on your desktop for it.

Like this:
```

#!/bin/sh
LANG=en_US
mc

```

save it say mcwrapper_lang.sh
then set it to executable then make an icon to it onto your desktop
after it you can simple start mc with klikk on its icon

cheers

---

