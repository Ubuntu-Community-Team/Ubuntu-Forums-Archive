---
title: "What in the world is wrong w/ my Ubuntu?!"
date: 2007-03-21
forum: General Help
---

### Post by billdotson on 2007-03-21
I am running Ubuntu 6.10 and I was using avidemux to save a video file.  After that I close it, try to open the video file and Ubuntu freezes.  I have a Core 2 Duo and DDR2 2GB RAM and my memory usage was about 85% w/ 95% use of the swap file!  For the past half hour it has been so sluggish that it takes about 3 minutes to open a properties window of a file.  I have NEVER had my RAM usage be that high, even while running a PC game in Windows (as far as I know) and it just seems ridiculous that Ubuntu is using that much memory.

What the heck? and my internet is also not working anymore (works in Windows), I have another thread about that issue.

Ubuntu is making me extremely angry, as for awhile it worked fine and randomly it seems it just freaks out and won't do anything.  It quit burning and/or formatting DVD/CDs a couple weeks ago, what is going to happen next?

---

### Post by hikaricore on 2007-03-21
My guess is that the video conversion software process that avidemux was being a front for never actually closed.

When something like this happens it's best to check this from terminal:

```
top
```

You'll be able to see the applications and services using the largest amount of memory and cpu power, and narrow down the issue.

If you find top hard to read, try installing htop:

```
sudo apt-get install htop
```

Which is color coded and easier to look at.  :)

If you don't like either just goto System/Adminitration/System Monitor to see all this info in GUI mode, tho this restricts the info you are actually able to see, but is more user friendly.

---

