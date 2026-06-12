---
title: "[aoss]Can it be done automatically ?"
date: 2005-10-26
forum: General Help
---

### Post by djib on 2005-10-26
Hello,
I lauch firefox using ```
aoss firefox
``` to get the sound in flash animations in firefox, even when using other softwares like rhythmbox that use the sound.
Is there a way to automatically redirect oss output to alsa without havind to use aoss (or at least without having to write it down).
Thanks

---

### Post by stuporglue on 2005-10-26
Easiest way is probably just to edit your firefox launcher buttons. For the one in the menu bar, just right click and choose "properties". 

Change the command "firefox %u" to "aoss firefox %u" and that button should launch it the way you want. 

You can do a similar thing in the Applications menu, but you have to use SMEG (aka. 
"Application Menu Editor" in System Tools sub menu.)

---

### Post by djib on 2005-10-26
Thanks, I did think of that. ;) 
What I meant is there a way to make all programs using aoss without having to explicitely tell them ?

---

