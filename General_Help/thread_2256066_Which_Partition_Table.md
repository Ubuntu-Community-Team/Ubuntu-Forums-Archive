---
title: "Which Partition Table"
date: 2014-12-09
forum: General Help
---

### Post by orsome1 on 2014-12-09
I have a micro server for my HTPC - Ubuntu 12.04.
I have installed a new 3Tb drive to use as a time machine backup drive for my mac. My first problem is which partition table should I be using to format the drive as hfs+, as I understand Time Machine will only work with hfs+ system
I am using GParted and have tried GPT but when try create partition I cant access hfs+ as its greyed out

the other drives on the server are formatted ext3

---

### Post by ian-weisser on 2014-12-10
You must use GPT if you want to use more than 2TB.
hfs+ compatibility is provided by the 'hfsplus' package, available in Software Center. That should un-gray the option.

---

### Post by Riback on 2014-12-12
worked thanks
just need to know get the Mac to see this Drive - not having much luck so far

---

