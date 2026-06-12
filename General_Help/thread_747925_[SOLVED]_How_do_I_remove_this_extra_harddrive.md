---
title: "[SOLVED] How do I remove this extra harddrive?"
date: 2008-04-07
forum: General Help
---

### Post by sTpny on 2008-04-07
Hi All, 

I've got two hd's in this old dell gx1 350, a 60 gig, and a 10 gig.  The 10 gig has only /opt and a swap partition, and I'd like to take it right out of there. Whats the proper procedure to do that? Also, I'd like to adjust the partitions on the 60 gig, but when I try to adjust (move or resize) any partition, partition editor tells me "can't, in use". What am I doing wrong?  

TIA

Tony

---

### Post by tamoneya on 2008-04-07
The way i would do it is to pop in the live CD and copy the contents of the /opt partition into /opt on your root partition on the 60GB.  Then I would create a swap partition on the 60 GB with gparted. I think the reason why you were having trouble resizing partitions previously is because they were already mounted.  Do this with all of your partitions unmounted and you should be able to resize your partitions as necessary.

---

### Post by tubasoldier on 2008-04-07
I would simply reinstall the OS to the 10gb hard drive and leave the entire 60gb to be my /home partition.

---

### Post by roachk71 on 2008-04-07
Inconvenient, but that is the safest alternative. The package database would be corrupted by the former option, and this could cause serious problems.

---

### Post by sTpny on 2008-04-10
Hi people, 

I don't actually like either idea. I need the 10 gig for another computer, and I wouldn't want to hear the sound of my package manager makes when it broken ;)  Is there a command to output what is installed to a file so that it could be reinstalled after?  Most of my personal stuff is just text files, and I would have to export my evolution accounts, but I'm sure all my personal stuff would fit on to one CD.  If there is a way I can just reinstall, and then reinstall the same packages that I already have, then I could do that. That way might be best actually, because then I wouldn't have to worry about something messing up again later because I forgot to do something, like edit my fstab, which nobody mentioned. 

Anyhow, is there a command to save a list of the currently installed packages to a file, so that those same packages can be reinstalled later? Certainly there must be, but what is it?

Thanks again, 

Tony

---

### Post by logos34 on 2008-04-10
you don't need to reinstall.  Just copy the contents of the /opt dir to your root partition on the 60 gig.  Then take out the separate line for /opt in fstab.  Use the ubuntu livecd or gparted livecd to add a swap partition on the 60 gig drive.  Again, edit swap entry in fstab.  

If you still want to reinstall, use **AptOnCD** to save your installed deb pkgs.

---

