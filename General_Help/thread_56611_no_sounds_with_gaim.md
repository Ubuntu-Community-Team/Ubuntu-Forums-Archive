---
title: "no sounds with gaim"
date: 2005-08-13
forum: General Help
---

### Post by DarkManX4lf on 2005-08-13
ok so i had to compile gaim my self a while back because i wanted to get the xfire plugin, i compiled and i installed and gaim works but it has no sound...i checked in the settings if the sounds were enabled, and they are. i cant even preveiew a sound for an event....how do i get the sounds to work ?

---

### Post by gylf on 2005-08-13
You could try switching the method to "command" under the sound preferences and putting something like:
```
play %s
``` 
in the field under it.
you'll know when its working when you can sucessfully test a sound in that same screne.

---

### Post by DarkManX4lf on 2005-08-13
thanks that worked !

---

### Post by jimarko on 2005-08-16
For all the Kubuntu ninjas out there that use ALSA 

use  ```
aplay %S
``` in the 'command' box, and you'll be set :)

---

