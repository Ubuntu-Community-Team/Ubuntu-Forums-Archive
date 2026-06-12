---
title: "Keyboard layout has Misplaced Keys"
date: 2008-06-17
forum: General Help
---

### Post by Silpheed2K on 2008-06-17
Here's the problem... I code.. and I type at a good speed but it seems that some of the keys on my keyboard are misplaced.
It baffles me.. so I tried changing the keyboard settings to what Windows XP was set to... Microsoft Natural.
Any variant of those settings didn't work.

When I hit the \ key it makes <
when I hit the actual , key with shift it makes <

is there any way to correct these minor misplaced keys so I can code and type in comfort?

---

### Post by wpshooter on 2008-06-17
What kind of keyboard is this you are using ?

Are you sure that it is not your fingers that are misplaced ?

Because on my keyboard if I was to do shift + the "," key then < is exactly what I am supposed to get !!!

If the "\" makes >, then are you sure that you don't just need to replace a defective keyboard ?

---

### Post by Silpheed2K on 2008-06-18
I know that's what you're suppose to get but my point is I have 2 keys that make <..
if I hit shift with the \ key it makes >
It's not a defective keyboard... all the other keys work fine except for this one it seems. I just want to reprogram that key so I can easily remember  where to go to I can make escape sequences (\n \t \a)

Also I dont know what kind of keyboard this is.. it's just a strange black unbranded UK keyboard (i live in america.. above my 3 is the sign of the british pound not #)
I'm fine with my 3 being missplaced as # but I want my \ to be \ cause I always go for it.
Thanks to you and anyone who helps.

---

### Post by cariboo on 2008-06-18
Waht type of keyboard did you select during installation, because that makes a difference.

Jim

---

### Post by Silpheed2K on 2008-06-18
US Layout because that works completely fine with this keyboard and doesnt confused me. (i dont want to use the poiund sign.. all that is irrelevant i just want the key reprogrammed to be something else)

edit: by the way it always works fine in Windows XP and I use the USA layout on there as well.

---

### Post by Silpheed2K on 2008-06-18
I fixed it... the solution is to use a program called xkeycaps and then execute it via terminal.
```
sudo apt-get install xkeycaps
xkeycaps
```
modify the keys then select Write Output. (preferably just the Changed Keys not all)
This is so everybody knows next time... I fixed it and I'm happy now.
xkeycaps... modifies keyboard layout and remaps keys.. peace

---

