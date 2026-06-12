---
title: "Can't change resolution in grub/videoinfo not responding"
date: 2018-07-01
forum: General Help
---

### Post by EvlZrglng on 2018-07-01
I am running (or attempting to) 18.04 on a Yoga 920 with 4K screen.  
Everything seems to run well apart from the scaling or some applications and the bootloader.  The applications I can work my way around and have it bearable, however the bootloader is very hard to use.

I have tried a few different things, however, when i go into grub and type videoinfo there is no feedback.  It just goes to a new line and acts as if nothing happened.  How can I fix this so I can have a different bootloader resolution without compromising my desktop resolution.  

I am new to Ubuntu so unfortunately I don't know what  a lot of terms mean and how to do/access a bunch of things.

---

### Post by Bashing-om on 2018-07-01
EvlZrglng; Hello -

Try as:
```

videoinfo

```
See: [https://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution](https://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by EvlZrglng on 2018-07-01
weird.  I eventually got it to work.  I don't know why videoinfo started to work now, but it did so I got to change it to 640x480.  Thanks for the help!  Now to figure out how to add fractional scaling.

---

