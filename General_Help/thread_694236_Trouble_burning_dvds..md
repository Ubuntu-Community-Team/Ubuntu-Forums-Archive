---
title: "Trouble burning dvds."
date: 2008-02-11
forum: General Help
---

### Post by kesuki on 2008-02-11
Okay, the built-in cd/dvd maker was hopeless, it stopped burning after about 600 mb, and locked up the drive so i had to reboot to eject, even after i exited the burning app. 

btw,the built-in burns cd-roms just fine, it was burning a data dvd that toasted it. 
 
so then i tried k3b for security reasons i didn't want the dvd to be writeable after it was burned, but k3b lacked a 'finalize disc option' so i just choose 'no multisession' the disc seemed to burn fine, although unlike in windows the green light on the burner went out about 12 times. in windows the green light never goes out. but the disc failed 'verify' right away, and none of the files were retrieveable from the dvd. 

i made an image prior to burning and the 'image' burned at 16.40x my burner is a 16x burner... i was wondering if i have to set burn speed to 12x or slower? or should I create a multi-session and finish it right away after burning my data? for security reasons i want the discs to be unwritable, because 'second' sessions can be written by root-kit software automatically, under both windows and linux when discs are burned multi-session... (although i've only seen it happen on windows 'in-the-wild' technically a root'd linux machine could do the same thing and put a root kit installer in the second session as a default auto run when the dvd is inserted...)  

i actually have about 20 'dvds' that were affected by the rootkit in-the-wild that creates it's own rootkit installing session on multi-session capable dvds. although it was not on every cd or dvd burned by that system, it was on enough to force me to reburn the whole lot, and i thought it would be 'safer' to do so from linux, but now i can't get any linux dvd burning software to run right.

---

### Post by kesuki on 2008-02-11
my second attempt i had firefox open and i think that caused the second one to fail, and i dont have any more dvds to try here, (i brought 3 with me, and they're all coasters now)

that one i made without an image at 12x, and even with firefox closed, it fell back to 4x speed (the default when my burner 'activates' buffer underrun protection) and Still at 4x speed the green light would go out.  this time, the dvd claims to be blank, but only has 171 mb 'free'

---

### Post by kesuki on 2008-02-11
correction, the disc has 171mb free, but it 'hangs' on trying to determine freespace.

---

