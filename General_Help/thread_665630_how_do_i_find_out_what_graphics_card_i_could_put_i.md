---
title: "how do i find out what graphics card i could put into my computer"
date: 2008-01-12
forum: General Help
---

### Post by duncan.hawthorne on 2008-01-12
hi

i think i have an agp graphics slot (stress: i think) on my motherboard which is empty, and am currently using an onboard via unichrome graphics card

i want to buy a new agp graphics card, but have read that not all agp cards fit into all slots. how can i find out which graphics cards my computer would support? is there some command in terminal to do this?

maybe if there is a command to find out my motherboard name i could look for the specs on the internet or something, to find out about graphics cards....?

any help with either of these?
:)

---

### Post by danwood76 on 2008-01-12
The easiest way would be to take the side off the PC and look for the motherboards name and manufacturer.

as long as you agp slot can support 8x then it will be fine, it would have to be a very old motherboard to not support 8x.

regards,
Danny

---

### Post by gsiliceo on 2008-01-12
Yeah find out the name of your motherboard, and then find the specs using google, the manufacturer should have information about its capabilities, once you know that, find a few graphic cards that suit your budget and then search their names here in the forum, to see if its compatible and how easy will be to install.
Thats what i did to get mine anyway :)

---

### Post by dcstar on 2008-01-13
> **duncan.hawthorne said:**
> 
..........
maybe if there is a command to find out my motherboard name i could look for the specs on the internet or something, to find out about graphics cards....?


```
sudo lshw | less
```

---

