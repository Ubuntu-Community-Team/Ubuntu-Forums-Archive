---
title: "Hard drive suddenly filled with invisible files"
date: 2008-03-30
forum: General Help
---

### Post by andymushu on 2008-03-30
Since this is a kind of hard problem to explain, I'll just start from the beginning. I recently deleted /usr/local/share by accident, and after gimp wouldn't start, i decided to try to fix this. I downloaded photorec, which found over 500,000 deleted files on my hard drive. After realizing that this was far too many files to sort through (along with the 1250 folders they were stored in), I decided to delete the folders. They were owned by root, so I opened nautilus as root and deleted all the folders. 

Now for the interesting part. Later, while checking gparted, I saw that it displayed the used space on my partition as 113 out of 115 gigabytes. I immediately knew something was wrong, as only a couple of hours ago only 29 GB were used. Then I opened disk usage analyzer to see which files were using such an absurd amount of space, and discovered that no such files existed. My root directory was only using 28.1 GB. So somehow my hard drive is filled with 113 GB of files, even though my root directory is only 28 GB. 

Does anyone know how to fix this? I tried checking the trash, I ran fsck from a live cd, and nothing seems to fix it. Sorry for the long post, but I wasn't sure how much was relevant and I figured the more information the better. I also attached a screenshot of disk usage analyzer, to better explain it.

Any help would be much appreciated.

---

### Post by Shazaam on 2008-03-30
Have you looked in root's ./Trash yet? Or in Lost & Found? Remember to enable hidden folder view when you open nautilus (Ctrl+H).
You need to be root to delete anything from root's trash folder. Open terminal, type this in....
```
gksudo nautilus
```
This code will open nautilus with FULL ROOT access so be VERY careful while running it. If you delete something it's gone FOREVER (well, almost).

---

### Post by andymushu on 2008-03-30
Thanks for the reply. I did check both my trash and the root trash with hidden folders turned on. I just checked lost and found as well. None of them had anything in them.

---

### Post by andymushu on 2008-04-01
Anyone?

---

