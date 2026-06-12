---
title: "Display &quot;configure screen settings and layout&quot; opens after closing and re-opening lid"
date: 2015-10-08
forum: General Help
---

### Post by cricri2 on 2015-10-08
hello,  I saw that this bug has already been reported similarly but not identically.  In my case one or more windows of the screen settings manager appear only after re-opening the lid (in the other thread it appeared all the time independently of closing/opening).  I have deactivated already the suspending functions on lid closing (to keep music playing f.ex.). I also tried to check or uncheck "configure new screens" but nothing changes.  I have the german version of Xubuntu 14 LTS.  ps : to be able to switch off suspending on lid closing, I had to supplement the light locker by a command I found in a forum (I don't remember, sorry), to make the light locker functions work correctly.  thanks Cri  pps : by the way, can anybody explain me why do I appear as "cricri2" when logging here ? my user name is CriCri...

---

### Post by Toz on 2015-10-08
>  In my case one or more windows of the screen settings manager appear only after re-opening the lid
Your system is sending out an XF86Display change event and Xfce is picking up and acting on it. A quick fix for this is to go to Settings Manager > Keyboard > Application Shortcuts and remove the XF86Display shortcut.

>  pps : by the way, can anybody explain me why do I appear as "cricri2" when logging here ? my user name is CriCri... 
Create a new thread in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123") an admin will fix that for you.

---

### Post by cricri2 on 2015-10-08
ooh thanks, this seems to work !! (how do I label it "solved" ?) for the user name, no problem, I was just surprised, but I don't really care.. thank you !

---

### Post by Toz on 2015-10-08
> **cricri2 said:**
> (how do I label it "solved" ?)
Select "Mark As Solved" from the "Thread Tools" link above.

---

