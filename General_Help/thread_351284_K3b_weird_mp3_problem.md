---
title: "K3b weird mp3 problem"
date: 2007-02-01
forum: General Help
---

### Post by SmiLey497 on 2007-02-01
when i try make a mp3 cd and drag a file its lists it bigger than what is is, for example a 3.8 mb file is listed as 36.2 mbs, any suggestions

---

### Post by MoLE on 2007-02-02
Given the difference in file sizes (approx one order of magnitude), I suspect that K3B is assuming you want to make a normal audio CD, rather than a data CD with lots of mp3 files on it.  

K3B is factoring in the conversion process from mp3 to raw (wav) audio before burning, which is approximately 10:1 for mp3s.

K3B is pretty clever at trying to guess what result you're trying to achieve with drag and drop functions.

What kind of CD are you trying to make - one that will play in normal CD players, or one that will play in an MP3-enabled CD player?

---

### Post by SmiLey497 on 2007-02-02
yeah i realized that i had to make a data Cd in order put lots of songs in mp3 format, they shoul dof been a little more clear on that :KS

---

### Post by jeremy on 2007-02-03
> **SmiLey497 said:**
> yeah i realized that i had to make a data Cd in order put lots of songs in mp3 format, they shoul dof been a little more clear on that :KS

It is quite clear, audio cd is one that will play on any cd player, data cd is for storing files, including mp3's.

---

### Post by SmiLey497 on 2007-02-03
um no im used to burning mp3 cds in windows and there is always a subsection of audio Cd that says to make an mp3 cd

---

