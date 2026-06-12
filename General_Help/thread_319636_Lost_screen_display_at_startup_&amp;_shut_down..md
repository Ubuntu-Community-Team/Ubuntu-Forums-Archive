---
title: "Lost screen display at startup &amp; shut down."
date: 2006-12-16
forum: General Help
---

### Post by Mr_Roodog on 2006-12-16
I've been enjoying Ubuntu for a while now but am a novice. When I first loaded it up and ran Ubuntu there was a progressive listing on screen to say what was happening, the same for when shutting down. I no longer get either, although sometimes I think I can see a  fast flash onscreen when shutting down. The only thing I have changed is GRUB so my PC first boots into XP unless I select Ubuntu.  Any clues on how to get the loadup / shutdown progress screen would be appreciated.  :confused:

---

### Post by aidanr on 2006-12-16
you have to remove the option "quiet" from the entry in /boot/grub/menu.lst

i tried it a while back and the text came up fine, but it was blue and therefore looked kinda ugly with the edgy usplash, although if you look hard enough there's probably a way of changing it to orange if it bothers you

---

### Post by Mr_Roodog on 2006-12-17
Thanks for that - will give it a try when I've worked out how to edit "menu.lst" Told you I was new to this eh! Cheers..........

---

### Post by aidanr on 2006-12-17
open a terminal and type "sudo gedit /boot/grub/menu.lst", type in your password and then edit the file, the text editor should make a backup of the file called "menu.lst~" (unless you've turned off that feature, it's on by default), should you need to restore it

---

