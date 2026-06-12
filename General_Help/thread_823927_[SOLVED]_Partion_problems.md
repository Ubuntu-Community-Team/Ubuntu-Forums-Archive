---
title: "[SOLVED] Partion problems"
date: 2008-06-09
forum: General Help
---

### Post by L337_K3y5 on 2008-06-09
I have no idea if I'm doing this right, because I have trudged screen on the manual part of the partioning process, and I don't want to accidently install over my Vista....I still want to have it for other things you know.  My harddrive is split up into different partions, one is Drive C:  Vista OS and the other is Drive D:  Data....I wanted to place Ubuntu onto the Drive D to separate it.  Here is the picture of what I got to:
[IMG]http://i302.photobucket.com/albums/nn102/Keyblade_frog/Screenshot.png[/IMG]
Hopefully you can see that In the list on the left it shows that DATA is /dev/sda5  while Vista is /dev/sda2  I have figured that the Data partion is /dev/sda5...but the mount point on the edit partion screen totally lost me :confused:.  Hang with me 'cause this is my first semi-transition from M$ to Linux.  Also no, my wireless internet is not working on it, so I had to plug it into the router to put the pic. online.

---

### Post by cszikszoy on 2008-06-09
The mount point isn't what you want to do - yet.  First you'll have to resize /dev/sda5.  When you resize /dev/sda5 you'll be left with a lot of unallocated space.  This is fine - you should be able to install ubuntu now and just tell it to use the unallocated space.  It should take care of all of the mount points for you.

---

### Post by L337_K3y5 on 2008-06-09
[IMG]http://i302.photobucket.com/albums/nn102/Keyblade_frog/Screenshot-1.png[/IMG]
NOw I'm having this problem...Should I let it resize the partition, the one it says, and is bubbled, which is partition 5 or /dev/sda5?  :confused::confused::confused:

---

### Post by cszikszoy on 2008-06-09
You have the correct option selected.  Partion #5 *is* /dev/sda5.

---

### Post by L337_K3y5 on 2008-06-09
Thank you for helping me install Ubuntu, I just got it installed, and I'm using the Firefox 3 beta 5 browser to type this now, I think I'm converted...I love Linux now.:KS

---

### Post by cszikszoy on 2008-06-09
No problem - glad to help!

---

