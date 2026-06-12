---
title: "Weird SWAP problem - Hardy"
date: 2008-05-18
forum: General Help
---

### Post by kdx on 2008-05-18
OK, I installed Hardy on my old XP partition the other day.  I'm currently dual-booting my new Hardy installation along with my old Feisty installation.  

For some reason, the swap isn't being used by Hardy.  I looked in /etc/fstab, and I have the correct UUID in there, and it is supposedly set up correctly.  

I'm wondering if the problem might be because I'm trying to use the same swap partition as the one I had been using in Feisty.  Would that cause problems?  My computer reads that it's there, and that there's free space, but it just won't use it.  Meanwhile it's killing my RAM.

Any ideas?

---

### Post by jimmy the saint on 2008-05-18
How much RAM do you have?  If you have enough that it is not all being used, there is no need for Hardy to use your swap.

---

### Post by sdennie on 2008-05-18
It should be ok to share swap between different versions of Ubuntu as long as you don't hibernate to the swap partition, start the other version and then expect to be able to resume from the first version.  As for swap not being used, that's a good thing.  If you are coming from a Windows background, you are probably used to Windows aggressively swapping stuff to disk.  Linux doesn't do that by default and it's not really needed (presumably because it's not expecting every app to leak memory).

---

### Post by kdx on 2008-05-18
I've been using Feisty almost exclusively for the last year, which lead to my decision to completely wipe Windows off my computer.  Normally I'd have 3-20% of my swap used while running Feisty.  I just find it disturbing that in Hardy my RAM usage will be up near 75-80% and the swap usage won't budge.  My computer tends to slow down once my RAM usage gets above 65-75% or so, especially while trying to watch videos.

I've been using Conky to display my statistics, so I'd see my swap usage every day.

I have 1GB RAM.

---

### Post by kdx on 2008-05-18
OK, I just tried really loading up my RAM to see what happens.  I did a GIS for as many extra large F-22 pictures as I could find and opened all of them up.  Once I was done, I checked my conky output, and it said that I was using about 70% of my RAM and 1% of my swap...so apparently there isn't an issue.  I guess I was just paranoid, because I had been having some problems with FF3b5, and it seemed that others who were having problems stemmed back to RAM and swap issues.

Thanks for your help.

---

### Post by sdennie on 2008-05-18
I think that "swappiness" might be more conservative with newer kernels.  I was using a machine with 1G of RAM the other day and I was specifically trying to see what I would have to do to make the machine start using swap.  It took a lot of effort.

---

### Post by kdx on 2008-05-18
That's what I was thinking.  I didn't put Gutsy on this machine, so I hadn't really kept up with the changes that had been made.

---

