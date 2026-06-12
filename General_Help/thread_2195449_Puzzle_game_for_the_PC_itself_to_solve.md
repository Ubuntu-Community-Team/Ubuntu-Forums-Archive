---
title: "Puzzle game for the PC itself to solve?"
date: 2013-12-24
forum: General Help
---

### Post by crazymonkey05 on 2013-12-24
i want a program like that 1000*1000 rubics cube program to see how long it would take my pc to solve it...i have scoured the internet and cant find a single puzzle that tests the pc. please help me out with one

---

### Post by john_ladasky on 2013-12-24
Bitcoin mining? ;)

---

### Post by crazymonkey05 on 2013-12-26
i dont want a game that the user plays but the pc itself and i also dont want one thats based on framerate, thanks and john that has nothing to do with the topic

---

### Post by Toz on 2013-12-26
> **john_ladasky said:**
> Bitcoin mining? ;)

> **crazymonkey05 said:**
> thanks and john that has nothing to do with the topic

I think @john_ladasky's reply was a little tongue-in-cheek referencing the processing power and time required to mine bitcoins.

How about timing the amount of time for your computer to calculate Pi to a set number of decimal points? For example, to time how long it takes to calculate Pi to 5000 decimal points:
```
time echo "scale=5000; 4*a(1)" | bc -l -q
```
...results on my laptop are:
> real	0m24.426s
user	0m24.430s
sys	0m0.000s


You can change the number of decimal points by changing the value 5000.

---

### Post by crazymonkey05 on 2014-01-13
i will definately try this toz thanks for the suggestion

---

