---
title: "No Sound in Ubuntu"
date: 2007-09-09
forum: General Help
---

### Post by circuz_phreak on 2007-09-09
I have no sound in Ubuntu, however when I put my headphones in the jack, works like a charm.  Im going to check my windows settings and see if it´s muted there.  Do windows settings carry over to this OS as well since they´re both manipulating the same hardware?  Any suggestions or help would be great.

---

### Post by prince_niceguy on 2007-09-09
i used to face similar issue in my toshiba where in the windows setting were carried forward at hardware level. not sure if you too are facing the same issue.

what is your hardware?

---

### Post by circuz_phreak on 2007-09-11
Not sure about my sound card, but I even made sure my windows settings weren't muted or too low or anything like that.  So that's not the issue, and when I plug headphones in the volume works fine.  Strange...

---

### Post by notwen on 2007-09-11
Press ALT+F2 and in the text field type 'alsamixer' and once you're there, verify that all of your volume options are turned up.

---

### Post by eggdeng on 2007-09-11
A lot of people have had this problem with Intel HDA cards. Post the output of ```
lspci | grep Audio
``` and ```
aplay -l
``` If your card is  Intel HDA, take a look at [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")

---

### Post by circuz_phreak on 2007-09-11
Thanks guys, got it working after a bit of troubleshooting.  It was an Intel HDA.  It´s insane how many problems like these i´ve ran into running ubuntu on my laptop.  Thanks again!

---

