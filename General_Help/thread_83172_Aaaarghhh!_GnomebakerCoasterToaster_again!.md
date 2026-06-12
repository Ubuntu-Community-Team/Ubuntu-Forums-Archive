---
title: "Aaaarghhh! Gnomebaker/CoasterToaster again!"
date: 2005-10-28
forum: General Help
---

### Post by xmastree on 2005-10-28
I wanted to make a DVD containing lots of MP3s. I dragged the various folders containing what I wanted into the window in the lower portion of gnomebaker's window. Then a few more, and more until the disc was full.

Then I burned it.

Reloaded it to look at the result, and it's a complete mess:  :confused: 
```
chris@ubuntu:/media/cdrom1$ ls -l
total 116729
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 01 - Close Your Eyes
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 02 - Love is The Tender Trap
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 03 - Let Yourself Go
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 04 - Dreamsville
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 05 - In Love Again
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 06 - The Boy Next Door 

-r-xr-xr-x  1 root root 4044676 2004-11-07 20:39 07 Claudia Claudia - True Colors.mp3
-r-xr-xr-x  1 root root 4439647 2004-11-07 20:40 08 Michael White Project - One Last Cry.mp3
-r-xr-xr-x  1 root root 5142237 2004-11-07 20:41 09 GTS - Baby Come To Me.mp3
-r-xr-xr-x  1 root root 5315690 2004-11-07 20:41 10 Fantastic Plastic Machine - Steppin' Out.mp3
-r-xr-xr-x  1 root root 4818318 2004-11-07 20:42 11 Estancia - Breakout.mp3
-r-xr-xr-x  1 root root 3551484 2004-11-07 20:42 12 D'Influence - Rock With You.mp3
-r-xr-xr-x  1 root root 4551660 2004-11-07 20:43 14 Kathy Troccoli - I Want To Know What Love Is.mp3

-r-xr-xr-x  1 root root       0 1970-01-01 08:00 Cafe del Mar
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 Chilled Ibiza
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 Chillout session
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 Classic Chillout 2 (Disc 1)
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 Classic Chillout 2 (Disc 2)
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 Classic Chillout (Disc 1)
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 Classic Chillout (Disc 2)
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 Closer
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 Disc 1
-r-xr-xr-x  1 root root       0 1970-01-01 08:00 Disc 2
chris@ubuntu:/media/cdrom1$

```If you notice, there aren't any directories. As I tried to burn it, there would be no files in the root, everything would be in directories, or further down. Maybe four levels in places.
I've snipped the above a little, but basically the first 6 lines should all be subdirectories of Stacey Kent, which should appear in the root.
The next bunch, tracks, should be in their own directory.
Third group, like the first, should be under 'chillout'

The files which appear to be there are unplayable too. :confused: 
All files are stored on a ntfs drive, but they play perfectly from there.

I would have used nautilus' built-in burner, but I like the usage graph in gnomebaker to see how full the disc is.

I had a [similar problem]("http://www.ubuntuforums.org/showthread.php?t=81295") recently, so I suppose I should have expected this...

I've looked at Gnomebaker's preferences, to see if there's a **move everything up one level and bugger it up completely** option checked, but there's no such option. :rolleyes:

---

### Post by zenwhen on 2006-08-26
It did the same thing to me and I have not used it since.

---

