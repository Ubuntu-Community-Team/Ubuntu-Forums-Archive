---
title: "cleanup grub bootloader"
date: 2006-12-09
forum: General Help
---

### Post by noktekniq on 2006-12-09
so i finally got dual boot to work. now when i boot my laptop it ask which OS i want to boot to. the thing i want to know is how to rename them? i want to be able to rename the names of the OS in the grub bootloader so it's neater. for example 

for windows xp it says
windows nt/2000/xp (something like that)
but i want to change it to "windows XP" 

how would i do that? without messing things up

thanks for the help

---

### Post by meital on 2006-12-09
```
sudo gedit /boot/grub/menu.lst
```
change only the lines that begin with the word "title".

---

### Post by noktekniq on 2006-12-09
thanks will try.

---

### Post by noktekniq on 2006-12-09
sweet works great. thanks 

was wondering how would i would make it go about looking like this

> 
"Linux Operating Systems:"
"ubuntu"
"ubuntu (recovery)"
"ubuntu memtest"

"other operating systems:"
"windows XP"

i tried doing it, but when i boot i won't see the bottom portion unless i press the down arrow

---

