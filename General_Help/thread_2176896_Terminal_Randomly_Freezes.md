---
title: "Terminal Randomly Freezes"
date: 2013-09-26
forum: General Help
---

### Post by rdJB8wd on 2013-09-26
**Problem:**
When running an application (for example via a launcher with terminal or straight from a terminal instance), the terminal randomly freezes. That is, the output stops in mid-stream after a random period.[IMG]http://ubuntuforums.org/asset.php?fid=244896&uid=1863112&d=1380210961[/IMG][ATTACH=CONFIG]246521[/ATTACH]

I discovered this while trying to run some long-running machine learning applications using a terminal.

Can anyone else reproduce this?
[B]
Terminals Affected:[/B]
gnome-terminal
mate-terminal

**Confirmed:**
Occurs with python test applications (see code below) or java applications. This also occurs randomly. See the sample code below (save to file and execute in a terminal). Using this code you can see the output freezes perhaps after a few minutes. In other words, the terminal scrolls output and then just stops mid-stream. To resume, you either need to:
[LIST=1]
[*]expressly select reset & clear or 
[*]double click on the terminal window or 
[*]UNRELIABLE--possibly just try to scroll back and fourth. 
[/LIST]

**What I Tried:**
Using various terminals, I have tried setting scrollback on, off, unlimited, or 512 lines--in other words, I have tried everything that I am aware to avoid some type of obvious "buffer" issue. I have also written teh test case below. Oddly, this occurs in any of the GUI terminals--but MIGHT not occur with xterm (I have never seen the issue occur with xterm so far).

**Test Code:**
```
import time

starttime = time.time()

i = 0

while(True):    
    i = i + 1
    print("Still working " , i, " " , time.time() - starttime)
```

**Specs:**
Ubuntu 13.04
MATE 1.6 (but also occurs in Ubuntu Default, GNOME3, etc.)
i7
32Gb memory
NVidia 760

---

### Post by rdJB8wd on 2013-09-29
**Possible Resolution:**

I confirmed that the terminal freezes randomly when running a terminal instance such as MATE Terminal or GNOME Terminal. The freezing or stopping did not occur with XTerm. 

This lead me to think that this was a video issue. Because I am using a new video card (Nvidia GTX 760) as of August 2013, I started to investigate the video card driver itself. I was apparently using an older version of the Nouveau Driver. I did not install the Nvidia proprietary drivers (currently 3.25).

I uninstalled Ubunut Nvidia Current and installed Nvidia 319 using Syntaptics (the option does not appear in Ubuntu SoftwareCenter). The install, even on a high-end machine took quite some time. I then selected the Additional Drivers and the NVIDIA binary xorg driver (NOT Nouveau). Again, this took a while to make the change.

Subsequent testing using the above test Python code shows the video driver update resolved the problem.

---

