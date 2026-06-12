---
title: "[SOLVED] Woobly windows seems very slow..."
date: 2007-10-27
forum: General Help
---

### Post by mike868y on 2007-10-27
all of a sudden today when i booted into ubuntu my woobly windows seems very slow... my actual computer isnt slow....programs run fast however when i move a window the wooble is "slow" is there a setting i can change?.. thanks for the help.

---

### Post by mcallenSchmee on 2007-10-27
If you have the compizconfig settings manager you can go to the wobbly windows plugin and set the 'Spring K' slider to max.

---

### Post by Crafty Kisses on 2007-10-27
> **mike868y said:**
> all of a sudden today when i booted into ubuntu my woobly windows seems very slow... my actual computer isnt slow....programs run fast however when i move a window the wooble is "slow" is there a setting i can change?.. thanks for the help.

See if there is anything using up a lot of resources.

---

### Post by mike868y on 2007-10-28
no theres nothing eating up alot of resources... it always stays below 5%. And i cahnged the spring k in gconf-editor to 10... didnt change... then changed it to 0.... didnt seem to change the slow affects. And it's not just the woobly windows.. its like any compiz effect. When i try to pop up a menu they pop up very slowly... idk its kind of annoying lol.

---

### Post by mike868y on 2007-10-28
i reninstalled ubuntu... and it's still not fixed.. it was working perfectly before idk what happened. The only thing i can think of is that the default drivers changed? Im still on fiesty so i doubt thats it, are there alternative drivers? I have an ati radeon x300... please help! However some effects such as the dim effect when my password is requested are much smoother.. ubuntu just is not the same without desktop effects

---

### Post by Zalbor on 2007-10-28
Maybe you enabled "slow animations" by mistake? In the compizconfig manager ("Advanced desktop effects settings"), go to General options>Actions>General and check the combination. Is it one you could have pressed by mistake? Press it again and see it it goes back to normal speed.

---

### Post by mike868y on 2007-10-28
no thats not it.. I hit the hotkey for slow animantions and it just made them even slower.. unberably slow.. the why they are now just seem abnormaly slow.. thanks for the help tho.

---

### Post by mike868y on 2007-10-29
So i tried the ati restricted driver under restricted driver manager.. then when i went to use the dekstop effects it said that plugin wasnt installed? So i disenabled that driver and the effects stil seem slower.. idk

---

### Post by mike868y on 2007-10-29
bump... sory for the triple post

---

### Post by Crafty Kisses on 2007-10-29
> **mike868y said:**
> i reninstalled ubuntu... and it's still not fixed.. it was working perfectly before idk what happened. The only thing i can think of is that the default drivers changed? Im still on fiesty so i doubt thats it, are there alternative drivers? I have an ati radeon x300... please help! However some effects such as the dim effect when my password is requested are much smoother.. ubuntu just is not the same without desktop effects

How much RAM do you have?

---

### Post by chrisccoulson on 2007-10-29
You're not running full screen anti-aliasing are you? (if thats possible with the ATI drivers).

I've noticed that wobbly windows is very choppy when running anti-aliasing and antistropic filtering with the NVIDIA drivers, and it is the only plugin that behaves like this. I see strange behaviour with the wobbly windows plugin anyway (mentioned here: [http://ubuntuforums.org/showthread.php?t=576768]("http://ubuntuforums.org/showthread.php?t=576768"))

---

### Post by mike868y on 2007-10-30
I have a gig of ram.. and i dont think its the anti aliasing setting ( i have no idea where these settings are for an ati driver).. it WAS working perfect up until a few days ago.... and i trie the ati restricted driver but it wouldnt let me enable desktop effects?

---

### Post by mike868y on 2007-10-31
I'm pretty sure i fixed it! I stopped the water plugin from running and now the wobbly windows seem much snappier.

---

