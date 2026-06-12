---
title: "xchat shuts down on its own"
date: 2008-02-08
forum: General Help
---

### Post by masterofthemelee on 2008-02-08
Well the thread title is pretty much all I can tell you.  I installed it via the Synaptic Package Manager, I open it, it pops up, and immediately closes back down.

Help?  I've already tried reinstalling, and then uninstalling and doing a fresh install.

---

### Post by masterofthemelee on 2008-02-08
Bump, would really appreciate some help.

---

### Post by shirilover on 2008-02-08
Try starting xchat from the terminal and see what error is reported.

---

### Post by masterofthemelee on 2008-02-08
Segmentation fault (core dumped)

EDIT:  I have no idea if this is relevant or not, but I just realized that my computer hasn't made any noise since I turned it on.  I just tried to run a media player and Peter Gabriel doesn't seem to be doing much.  Every time I turn the media player on the volume control is set to zero (even though I can change it).  I also went into the sounds menu in the control center and testing out the sounds in there doesn't produce anything, though if I test the sound playback device it will beep.

---

### Post by zmjjmz on 2008-02-25
This has happened to me and a friend of mine.
It just segfaults immediately after started :/

---

### Post by Crafty Kisses on 2008-02-25
Hmmm, post the following output:
```
top
```
It would be interesting to see what's running at the time of the segfault.

---

### Post by zmjjmz on 2008-02-25
```
 4967 root      15   0 30380 3152 1888 S    8  0.3  67:35.04 NetworkManager     
 5896 root      15   0  544m 201m  14m S    1 20.5  67:17.41 Xorg               
 6217 zj1992    15   0 20224 8676 7280 S    1  0.9   3:46.73 multiload-apple    
20540 zj1992    15   0 82088  19m  11m S    1  2.0   0:00.49 gnome-terminal     
20560 zj1992    15   0  2364 1164  876 R    0  0.1   0:00.03 top                
    1 root      25   0  2952 1840  516 S    0  0.2   0:01.32 init            
```
The major runners before I start Xchat
```
20567 zj1992    35  10 12576 8768 3248 R   96  0.9   0:10.06 apport             
20540 zj1992    15   0 82252  19m  11m S    6  2.0   0:01.07 gnome-terminal     
 5896 root      15   0  566m 222m  14m S    5 22.7  67:21.11 Xorg               
 4967 root      15   0 30380 3152 1888 S    3  0.3  67:38.67 NetworkManager     
12114 zj1992    15   0 22996  16m 6892 S    1  1.7   2:29.99 compiz.real        
20562 zj1992    15   0  2364 1164  876 R    0  0.1   0:00.06 top                
20564 zj1992    18   0 53448  23m  13m S    0  2.3   0:00.55 xchat     
```
The major ones when Xchat segfaults. (taken just before Xchat quits, it takes me to a join server window, which freezes, then dies)

---

