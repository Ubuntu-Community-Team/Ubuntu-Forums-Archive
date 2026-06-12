---
title: "Script Baking"
date: 2006-12-18
forum: General Help
---

### Post by ZERO_SHIFT on 2006-12-18
I want to run a script with the following:

```
sudo killall esd
sudo -i 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit
et

```

In order to run Wolfenstein Enemy Territory. How can I make such a script.

And is there a way of running Wolfenstein Enemy Territory without the need of sudo first in order to save he settings?

Thanks in advance.

---

### Post by koenn on 2006-12-18
put everything in a text file, save it (eg eetstarter)
you want to get rid of the sudo 's - better & easier to run the whole script as root or with sudo


```
sudo killall esd
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
et
```

to make it executable : set the permissions to 'executable'
to run : create a launcher with "gksu etstarter " in "command" field
or run in terminal : sudo ./etstarter

---

