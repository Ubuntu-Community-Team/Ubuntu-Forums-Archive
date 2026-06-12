---
title: "hardy freezes with no specific app open"
date: 2008-05-23
forum: General Help
---

### Post by THEBIGEYE on 2008-05-23
just recently upgraded to hardy from gutsy (which worked like a dream) but now hardy has a problem for no apparennt reason the GUI freezes but i can still move the mouse but i cannot click any buttons, the other day i was watching a vid on you tube and the gui stoped me clicking buttons but the video kept playing happily away to its self. i have tried reproducing errors but they are just to random i have checked the temps of my machine and they are fine done a bit of googling and people were saying ff3 could be the problem uninstalled that and using other browsers but nope still freezing anyone had this problem or a poss solution looking into building a 2.6.25 kernel see if its the kernel cheers of any help.

---

### Post by aroch1 on 2008-05-23
Try running top in the terminal in the background and when it freezes, see what process is using all of the system resources.

---

### Post by Mighty_Joe on 2008-05-23
[Join the club.]("http://ubuntuforums.org/showthread.php?t=765510&highlight=ubuntu+freezes")
I had success [updating the kernel]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/227882") in Hardy, but I'm sticking with 7.04, which is stable on my hardware, until this problem is resolved.

---

### Post by THEBIGEYE on 2008-05-24
I have tried running processes on top and when it freezes the bloody window minimizes thus i can't restore it to full size because i can't grab the buttons but to reiterate i still have cursor movement is there any logs worth looking at when i restart X with Ctrl Alt and Backspace (the only keys that work cant even drop down to command line with Ctrl Alt F1) 
cheers Ian

---

