---
title: "I've got 2 Cedega problems, please help"
date: 2007-07-07
forum: General Help
---

### Post by Joe88 on 2007-07-07
1) When I run the system tests in Cedega it says  my 64 bit Ubuntu is missing 32-bit emulation libraries - where do i get them and how do i set them up?

2) I click continue in the install window to install Medal of Honour allied assault, but nothing happens

---

### Post by dfreer on 2007-07-07
> **Joe88 said:**
> 1) When I run the system tests in Cedega it says  my 64 bit Ubuntu is missing 32-bit emulation libraries - where do i get them and how do i set them up?

2) I click continue in the install window to install Medal of Honour allied assault, but nothing happens

(1). Try this command, then run the test again:
```
sudo apt-get install ia32-libs
```
You may need to install more 32-bit libs, I'm not quite sure what Cedega requires.

---

### Post by Joe88 on 2007-07-08
Thanks for the reply, i did what you said and the tests are now working, my games are also installing now - i think i was just not waiting long enough. But i have one more problem which is that my Alsa test is failing, anyone know why?

---

### Post by Joe88 on 2007-07-14
My Alsa is now working

---

