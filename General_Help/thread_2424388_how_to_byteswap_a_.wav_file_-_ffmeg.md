---
title: "how to byteswap a .wav file - ffmeg?"
date: 2019-08-07
forum: General Help
---

### Post by Skaperen on 2019-08-07
i got a .wav file that is very highly distorted.  it sounds byte swapped.  does anyone know a way to fix this?  i have an old C program to do byeswapping but it requires raw format audio files (it would trash a .wav file).

---

### Post by Holger_Gehrke on 2019-08-08
SoundeXchange will swap bytes, see 'man sox', especially the option '-x'.

Holger

---

