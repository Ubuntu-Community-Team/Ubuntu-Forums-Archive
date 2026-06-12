---
title: "major display problem"
date: 2008-03-24
forum: General Help
---

### Post by theblackoilx on 2008-03-24
i have just recently installed kubuntu on my desktop and it was working fine until i installed some updates that had popped up. i am new to linux and dont know too much about it. i installed kubuntu with dual boot to still keep win xp. the problem i am having is that after the kubuntu screen loads, the screen is just black/blank. i am guessing something has happened to my display driver and it is not functioning correctly. i have an nvidia gforce 4 ti4200 graphics card which it installed a driver for and everything was working ok. it was this new batch of updates that has messed up everything.

another problem i find is that kopete seems to crash every time i try to log into MSN. is this not a good program to use for MSN? i had tried installing other MSN programs but i  do not know if theyll work any better because this display problem has happened and rendered kubuntu useless. 

i would appreciate any help as to how i can fix this issue since i am unable to do anything on this computer with a blank screen.

i am running the latest version, 7.10

---

### Post by alan34 on 2008-03-25
If you boot to a recovery consul from grub or when you get to your blank/black screen press
Ctl-Alt-F2 you should find a screen with a text login. Login then type

sudo dpkg-reconfigure -phigh xserver-xorg

If it ask you for a driver type pick vesa. Then go

sudo shutdown -r now 

You should have your desktop back although no restricted display driver which should be in
System - Adminstration go and try that again. At least now you will know how to recover
from any problems you may find.

Good luck

---

### Post by Chaositect on 2008-03-25
I have the same issue with an ATI x1950 pro.  I can login like normal even though I cannot see anything, and the main X window looks fine.  

Problem with removing the restricted driver is, it messes up the display all around.  (lines accross with shadow images like the old days when you got an incorrect frequency)  I can re-install / re-initialize and it's just like it was before. 

I have this same black screen on some other native linux programs, and wonder if it's shifting to a mode that doesn't work...  is there a way I can find out this mode and lock it out, or force the login screen to the proper mode?  I'm going to try windowed mode on some of the other programs and see if it helps, but I'd like full screen support too...

Thanks for the help Alan, and any more who reply.

---

### Post by mlapaglia on 2008-03-25
if you can't get to your xorg.conf you can try booting from a livecd and edit it manually. there are configs in it that control your monitors abilities and such i believe.

---

### Post by alan34 on 2008-03-25
For your video cards have you looked at this thread you might find your card(s) there

[http://ubuntuforums.org/showthread.php?t=361240](http://ubuntuforums.org/showthread.php?t=361240)

Good Luck

---

