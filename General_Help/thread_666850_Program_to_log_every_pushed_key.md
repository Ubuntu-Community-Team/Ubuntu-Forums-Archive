---
title: "Program to log every pushed key"
date: 2008-01-13
forum: General Help
---

### Post by dustman on 2008-01-13
hello!

i have a question, perhaps you'll find it childish or naive, but i have to ask nevertheless. Is there some program/widget for linux that can count all the keys i push? i mean if i input "The quick brown fox jumped over the lazy dog" it will record that 44 characters were inputed. 

Thanks!

Radu

---

### Post by articpenguin on 2008-01-13
i guessing your looking for a keylogger

i found one in synaptic but i didnt download it nor i have tryed it. 

do

> sudo apt-get install lkl

---

### Post by dustman on 2008-01-14
thanks for the info! i got it installed, and then tried to run it:
```
dustman@dustman-laptop:~$ sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o /home/dustman/log.file

Started to log port 0x60. Keymap is /usr/share/lkl/keymaps/us_km. The logfile is /home/dustman/log.file.
Segmentation fault (core dumped)

``` 
It's truly a marvel :lolflag: now that i know what i'm looking for, i'll just keep looking :)


Cheers!

Radu

---

