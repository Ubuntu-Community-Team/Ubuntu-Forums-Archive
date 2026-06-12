---
title: "pyrenamer : able to capture one number of a group of numbers?"
date: 2016-04-18
forum: General Help
---

### Post by kdford on 2016-04-18
Original file: "3072 - Foo.mp3"
Goal:  "lorem Foo - Disc 03 Track 072.mp3"

Given that {#} captures a group of numbers, I was hoping for a modifier (maybe numberic/positional), such as {#1} to capture first digit of the number, {#5} to capture 5 digits.  Or repeating capture symbols to have special meaning, as in {#}{##}

Such that I could do something like
ORIGINAL:   {#1}{#3} - {X}.mp3
RENAMED:   lorem {3} - disc {num2}{1} Track {2}.mp3


Is this possible?

---

