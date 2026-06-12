---
title: "Uninstalling Ubuntu disk shows less than is has"
date: 2008-01-19
forum: General Help
---

### Post by Solenoid on 2008-01-19
I want to remove my Ubutnu installation, it's not that I don't like it, but as for now I can't afford another hard disk and I want to play games.

The problem is that when I boot with XP's cd in and reach the partitioning screen I see about 130GB on it, but I have a 200049647616 byte hard disk (180GB), so what gives. My original installation was partitioned in 4: Windows XP, home, Ubuntu and Swap. What eats my hard disk, I want that space back. Fixmbr didn't do nothing and my Ubuntu livecd shows that the disk is 200049647616 byte.

Any help recovering those lost GB would be greatly appreciated.

I plan to reinstall Ubuntu later when I'll have another hdd.

---

### Post by pjkoczan on 2008-01-19
File system accounting data is part of the reason why you don't get "100%" usage out of a disk (in any filesystem), but that wouldn't explain a 50 GB disparity. You might have unpartitioned space, or the XP tools don't know its there for one reason or another.

If you could load Ubuntu somehow (a Live CD should be fine) and run some sort of disk usage analyzer (the "df" command from the terminal or a GUI program is in Applications/Accessories), it might give you an extra info to see where the problem may lie.

Also, an Ubuntu installation, on the whole, isn't that big. You might want to consider making a fifth partition for shared data and make it available to both Windows and Linux, and making the OS partitions for Windows and Linux relatively small (say 5-10 GB each). Get a little creative and you just might find you can have your cake and eat it too.

---

### Post by Solenoid on 2008-01-19
I think I got it: to get all the space on a "big" hard disk you need BIOS support and a minimum on SP1 or it will block at 128GB (even my drivers CD won't work below SP1 so no problems with the BIOS), I have been using the original XP CD which has nothing (an original that came with a Dell)... well, time to get an SP2...

---

