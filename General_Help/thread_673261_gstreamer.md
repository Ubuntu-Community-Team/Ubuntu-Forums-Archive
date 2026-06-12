---
title: "gstreamer"
date: 2008-01-20
forum: General Help
---

### Post by giok13 on 2008-01-20
k well ive had ubunut for like a couple of months but lately ive had some problems. the first problem is tht i cant login into my main account so ive been using root. but now i cant turn up the volume on my computer while in ubuntu. the volume works on windows vista but not in ubunutu. wen i press the short cut keys the volume icon pops up but nothing happens the volume doesnt go up. so thn i pressed the volume icon in the top rite corner and it gave me a error saying no volume control gstreamer plugin and or devices found. so how do i get my volume back. can i just reinstall gstreamer

---

### Post by slwory on 2008-01-20
Same problem

---

### Post by rosegarden78 on 2008-01-20
To activate Volume keys in XFCE you would need to install xfce4-mixer from Synaptic.  In KUbuntu make sure you have mixer, kmixer or volume-control installed.  Search for those terms in Synaptic to select the appropriate mixer.

---

### Post by slwory on 2008-01-20
> **rosegarden78 said:**
> To activate Volume keys in XFCE you would need to install xfce4-mixer from Synaptic.  In KUbuntu make sure you have mixer, kmixer or volume-control installed.  Search for those terms in Synaptic to select the appropriate mixer.

Thanks for the reply but that didn't work, for me anyway. (Ubuntu 6.06). I think my sound card isn't being detected. How can I make Ubuntu recognise it?

---

### Post by bw44 on 2008-01-23
> **slwory said:**
> Thanks for the reply but that didn't work, for me anyway. (Ubuntu 6.06). I think my sound card isn't being detected. How can I make Ubuntu recognise it?

Have you checked out this very useful thread?

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It helped me get my sound card (chip) working.  For example, it shows terminal line commands like ```
aplay -l
``` which should tell you if Ubuntu is recognizing your sound card.

Good luck and persevere! Sound cards can be tricky if they don't work "out of the box" when you install Ubuntu.

---

