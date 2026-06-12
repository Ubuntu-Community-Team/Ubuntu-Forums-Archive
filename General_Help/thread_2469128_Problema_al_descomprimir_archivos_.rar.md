---
title: "Problema al descomprimir archivos .rar"
date: 2021-11-20
forum: General Help
---

### Post by nacho-pgnp on 2021-11-20
Buenas noches.

Tengo un problema muy raro. Estoy corriendo Ubuntu 20.04, y al querer descomprimir un .rar de 258kb, el archivo resultante extraido termina pesando 58 gb! Cual es la explicacion para esto? Si alguien tine alguna ayuda se lo agradezo

---

### Post by Holger_Gehrke on 2021-11-21
Welcome to the forum!

Next time you post here please use English, we are more likely to understand your problem even from badly broken English written by a human than from a google-translation of a well written post in another language.

So - unless Google has messed up the translation - you're surprised by a 258kb rar archive getting uncompressed into several Gigabytes ? This is quite normal for highly redundant data. For example a megabyte of bytes with the value 0 will compress to less than three hundred bytes using xz (another compression tool).

Holger

---

