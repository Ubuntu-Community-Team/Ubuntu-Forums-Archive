---
title: "Lenovo E431 volume key is not working after update on ubuntu 12.04 LTS sucks."
date: 2013-10-14
forum: General Help
---

### Post by bensonfunglinux on 2013-10-14
Hi,

I recently installed ubuntu 12.04 LTS into my Lenovo E431.   Originally it works fine.  Typing F2 and F3 key can control the volume.  However, after update the whatever patches, the volumn key doesn't work and the birghtness key cannot work too.  And even Skype cannot install too.


I total lose confidence to this sucks ubuntu.

Please tell me how to fix it back .



thanks
Benson

---

### Post by varunendra on 2013-10-17
Might help if you post the kernel and the modules in use. That is, the outputs of -
```
uname -mr
lsmod
```

Does the software volume control work normally?

And for brightness, you should ask in a different thread as the title of this thread will probably get you no attention for that. It is always a good idea to keep different issues in different threads.

Feel free to post a link to it here if you start a different one. You may start with a detailed description and the output of this -
```
for i in `ls /sys/class/backlight/`; do echo -e "\n $i"; cat /sys/class/backlight/$i/{brightness,max_brightness,actual_brightness}; done
```

---

### Post by oldos2er on 2013-10-17
Moved to General Help.

---

