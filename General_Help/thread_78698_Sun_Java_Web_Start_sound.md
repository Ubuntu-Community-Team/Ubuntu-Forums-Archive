---
title: "Sun Java Web Start sound"
date: 2005-10-18
forum: General Help
---

### Post by bsantos on 2005-10-18
Just for reference, in case someone has sound issues with JWS and sound, I tried to use aoss to pipe JWS sound and it works well. I just had to make a simple shell script to call the javaws with aoss:

--(/usr/local/bin/javaws-aoss)--
#! /bin/sh
aoss javaws $1
--(endoffile)--

:)

---

