---
title: "Sound"
date: 2008-03-26
forum: General Help
---

### Post by k0rn on 2008-03-26
I have Ubuntu 7.10 and im not getting any sound at all. I was wondering if this might be a hardware issue or as simple as a configuration issue. And also im having problems with Rails. But thats a whole another story if someone has time for it.

---

### Post by JAPrufrock on 2008-03-27
First check to see if your sound hardware is installed and recognized:  open a terminal window and type the following command:  > discover sound
If your card/driver is listed, it's probably not a hardware problem.
If it's a software problem try opening up a terminal and typing: > alsamixer
then fool around with the controls.  You can also go to System/Preferences/Sound to test your sound card there.

also, check out this thread: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

