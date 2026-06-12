---
title: "Messed up HDD installing Ubuntu"
date: 2008-03-02
forum: General Help
---

### Post by Le 3eme Oeil on 2008-03-02
If this is the wrong place to post, just tell me because im new. 

Ok, so i was partitioning my HDD to make room from ubuntu.  So i took my 74Gb HDD (C: ) and took 30Gb from it and made G:.  Now, i was intalling ubuntu and it wanted me to partition that G: drive again.  So what ever i split that in half and it was installing ubuntu on step 5/7 but then i had to go to bed so i turned it off.
To make a long story short, my 74Gb HDD is now only a 44Gb HDD.  And that G: drive is no longer there.  Any way i can get that 30Gb back?? 

Edit: so now i basically want to make my 74Gb HDD that is now 44Gb back to 74Gb and then start fresh and intall ubuntu the right way.

---

### Post by Nzer24 on 2008-03-02
The space is still there, but it isn't formatted or being used. All you need to do is use the installer, but when you get to the partitioning phase, select "use largest contiguous free space". That should work. If not, use the program gparted (in System >> Administration >> Partition Editor) and remove all the partitions except for the windows one (it will be ntfs). Then try the installer again, using the largest contiguous free space.

Just as a guideline, don't just stop in the middle of installing an operating system.

---

