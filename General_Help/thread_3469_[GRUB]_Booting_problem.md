---
title: "[GRUB] Booting problem"
date: 2004-11-06
forum: General Help
---

### Post by goDez on 2004-11-06
I have used the search and google on this problem, but I couldnt find anything similar to my exact problem. Please take some time to read if you think you can solve my problem, had it before or have tips for me.

I can access GRUB. I can edit the config file by either gedit or grubconf. I am sure I have selected the right options (since the same options apply to my laptop, and it works there). The problem: GRUB won't boot into Windows XP Home. I have the option Windows XP Home into my bootloader, but when I enter it, all it states are the selected options I've put into the config file. It stops there, and does not boot into anything. I dont think the system froze, it just does not continue. I've currently configured my menu.lst for the win xp home entry as follows:

> 
title Windows XP Home
rootnoverify(hd0,0)
makactive
chainloader +1


Is it better if I install LILO? Or am I just doing something stupid here..

---

### Post by CapKrugers on 2004-11-06
I had this exact same problem. I solved it by setting the BIOS hard drive access mode to "Large" instead of "Auto". Try changing the hard drive modes in your BIOS; maybe you have something like "LBA" instead of "Large" that will work.

---

### Post by ispmike on 2004-11-06
[QUOTE=CapKrugers]I had this exact same problem. I solved it by setting the BIOS hard drive access mode to "Large" instead of "Auto". Try changing the hard drive modes in your BIOS; maybe you have something like "LBA" instead of "Large" that will work.[/QUOTE]
 Ditto to what CapKrugers said, I had the same problem and that fixed it.

---

### Post by goDez on 2004-11-07
[QUOTE=CapKrugers]I had this exact same problem. I solved it by setting the BIOS hard drive access mode to "Large" instead of "Auto". Try changing the hard drive modes in your BIOS; maybe you have something like "LBA" instead of "Large" that will work.[/QUOTE]

thanks alot! It boots into XP as we speak, i put it on LBA. (large gave weird errors tho :D)

I have a whole new problem now. Also a booting problem.
My ubuntu stopped booting :S
And i mean, as in, seriously not booting. I can boot it, and then it goes thru some starting up sequences like i always see before. It just stops at one point.
Using the Recovery mode doesnt help.

---

