---
title: "No sound!"
date: 2007-08-19
forum: General Help
---

### Post by causticsoul on 2007-08-19
I just installed Ubuntu, and I have no sound, I have a ATI Technologies Inc SB450 HDA Audio card, and I have no idea where to start.

---

### Post by waldorsockbat on 2007-08-19
Have you run update manager yet? that solved the problem for me after install.

---

### Post by causticsoul on 2007-08-19
It's running, I just thought there was somthing wrong with my drivers :P

---

### Post by waldorsockbat on 2007-08-19
My wifes laptop has that chip set in it and fiesty wanted to use the modem as the  sound card  but after updating the kernel it worked fine.

---

### Post by jusmurph on 2007-08-20
enter this in the terminal:
```
aplay -l
```

...and paste your results.

Also try looking at the alsa mixer and checking wheter things are muted etc by typing this in the terminal
```
alsamixer
```

If you get confused how to use it enter this in the terminal:
```
man alsamixer

```
Also have a look in: 
System > Preferences > Sound 
System >Preferences > Mulitimedia

---

