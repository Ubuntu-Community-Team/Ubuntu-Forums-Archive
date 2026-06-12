---
title: "System starts accessing hard drive, slows down to a halt"
date: 2007-12-12
forum: General Help
---

### Post by quadomatic on 2007-12-12
Usually, I can boot my system, and then everything works peachy. Then, once I start doing stuff thats memory intensive, like using Firefox and Thunderbird, or watching videos, after a little while, my system starts going slower, and my PC's hard drive starts reading a lot (orange light going off). Eventually, it just slows down so much that I can't move my mouse much at all. It bounces around like it's running like a slideshow. Eventually, mouse movements and keyboard presses don't appear to register.

The only way out of it is to reboot my system.

Does anyone have an idea why this is happening? Maybe my swap file is messed up or something? This development has happened only recently.

Can someone please help me out? Maybe I have to format my swap file or something?

---

### Post by Wiebelhaus on 2007-12-12
That's normally referred to as "disk thrashing" which is corrected by adding much more ram ( this day and age we're talking gigs)and increasing your swap space, but you may also be experiencing a failing hard drive run some harddrive & memory diagnostics from [UBCD]("http://www.ultimatebootcd.com/"). good luck.

---

### Post by quadomatic on 2007-12-12
I just decided to try and use up as much ram as possiible, and I think i figured out what's wrong.

I reached 700 MB of Ram usage, but by the time I broke 650MB, there was a slowdown. I saw that my computer wasn't using the swap partition at all. I think this has to do with me resizing my partitions, so that what used to be:

80 GB - ext3 partition
1..5 GB - Swap Partition

now looks like:

60 GB - ext3 partition
20 GB - FAT32 Partition
1.5GB Swap partition

Obviously something is wrong with my PC in it not using the swap file. How would I fix this?

---

### Post by Wiebelhaus on 2007-12-13
I'm not sure on how to increase your swap size or relocate it to another partition in linux , maybe this bump will help you get the answer your looking for.

Good luck mate.

---

### Post by fenx7 on 2008-05-09
I am also having the same issue. I also have 2GB RAM, and a a core 2 duo. System monitor reports about a 37% RAM usage and 4% swap file usage.

When the hd light comes on the application that I am using fades to grey to indicate it is unresponsive. After 2 or so minutes it returns to normal and all is fine. i don't think that the hardware is stressed, but maybe a software setting that needs to be adjusted.

Any ideas?

---

