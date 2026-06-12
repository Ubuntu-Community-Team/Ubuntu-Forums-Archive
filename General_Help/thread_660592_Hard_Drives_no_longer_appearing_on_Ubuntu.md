---
title: "Hard Drives no longer appearing on Ubuntu"
date: 2008-01-06
forum: General Help
---

### Post by ChCh on 2008-01-06
Hi all.  
I have installed ubuntu very recently an up until now have had no problems with it that i havn't been able to solve with common sense.
I am using a laptop that also has windows xp on it, and 3 drives - C, D and a new one I made to use for ubuntu.
On my ubuntu desktop right up until this afternoon there were C(system) and D(data) drive icons.  They are gone now, and when i try to access a file that was located inside one of the drives I get an error message saying location not found.
The drives are still visible on windows.
I can still see the drive I created for ubuntu installation.
The only thing I did between the drives being there and not being there was try to play a dvd and got a problem with unmounting.  Can anyone help, or will it be easier to re-install ubuntu? (Is this even possible?)
If there is an obvious solution to this problem and I just come across as an idiot, I am sorry.  I cannot see it.
Thanks in advance.


EDIT
Ok.  Found the reason.  For some reason windows had hibernated and not shut down and again, for some reason that fixed the problem.

---

### Post by kira. on 2008-02-04
HEEEEEEEEEEEEEEEEEEEELP

you seem to know the problem and how to fix it, so i was wondering if you could help me out, since I've come upon that exact same problem. Some error popped up on my windows, and when I rebooted into Ubuntu, my Windows drives had DISAPPEARED! It's making me quite sad, so I was wondering if you could help me?

thx much,

-guy in trouble

---

### Post by jan quark on 2008-02-04
try rebooting into windows again and see if the error occurs again and shutdown safely

it would be good to know that your drives are ok in windows

ops missed the edit

yes always safely shutdown

you can run 

```
sudo fdisk -l
```

to show all mounted and not mounted devices and post the result here

---

