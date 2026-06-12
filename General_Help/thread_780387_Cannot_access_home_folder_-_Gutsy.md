---
title: "Cannot access home folder - Gutsy"
date: 2008-05-03
forum: General Help
---

### Post by thorner on 2008-05-03
Hi,

I am having problems accessing my home folder. 
The problem only happens once the computer has been on for a while (about a day or so I think, sometimes less)

Problem actually started a couple months ago (on Feisty), and I had hoped that an upgrade to Hardy would fix it. No luck.

When the problem arises, everything on my desktop becomes inaccessible, and I cannot open my home folder. Problem happens using Nautilus, Thunar and Nautilus as root (gksudo nautilus). Nautilus/Thunar do not freeze (as I've read in other posts with similar problem) they just sit there trying to load the folder. I can close the window, or backup to root.

I can still navigate to the home folder using a terminal. Only fix for the problem seems to be a full machine reboot, logout/in doesn't fix the problem.

Your help is greatly appreciated.

---

### Post by DaddyX3 on 2008-05-03
I used to have this problem back with Feisty as well. The only thing that fixed this issue for me is to adjust the sleep functions within Ubuntu and/ or turn off all BIOS controlled power functions.

---

### Post by thorner on 2008-05-03
Checked my ubuntu sleep setting (System>Preferences>Power Management), it is set to "Never" go to sleep.
From what I can tell, the BIOS doesn't have any power management options turned on.

---

### Post by jimv on 2008-05-03
Have you tried creating a new profile?

---

### Post by thorner on 2008-05-04
no. should I? what might that accomplish?

---

### Post by jimv on 2008-05-04
I guess it depends.  If you upgraded from Feisty to Hardy, then it could be a problem with nautilus settings or something in your profile.

So try creating a new profile (just create a new user called test or something) and see if the same issues persist.

---

