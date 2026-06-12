---
title: "filesystems corrupt on each boot"
date: 2007-07-02
forum: General Help
---

### Post by santiagokq on 2007-07-02
i've been using ubuntu since 5.10 breezy, always updating to the newest versions, with no serious problems until now.  but about a month ago, when rebooting from windows xp, ubuntu wouldn't load, and gave me a "recovery console" instead (not even recovery mode).

i ran fsck, and after fixing many errors in most of my partitions (3 fat32, 5 ext3 total), i could boot it.  some days after that, i couldn't even get the recovery console, so i had to run fsck from a rescue cd.  and again, everything worked out ok.

now it's like every time i boot, i get a lot of filesystem errors, and i have to run fsck in order to run ubuntu (sometimes, i even get that recovery console again).  and this last time, it seems like some things have been corrupted: desktop fonts look too big, and titlebar icons are off-place.

is there anything i could do to fix this, or at least track the source of my problem?  or should i just format everything (excepting the fat32 partitions, which seem to be ok to windows), and re-install ubuntu from scratch?

greetings and thanks in advance,
santiago.kq

---

### Post by p_quarles on 2007-07-02
I can't offer much help, but I'll throw out a couple guesses. First, do you happen to have the software that allows you to read/write the ext3 partitions from Windows? If so, I would almost suspect that MSW is doing something funky to your Linux partitions (esp. since you indicated that this happened first after you rebooted from Win). 

I don't know how often you defrag your drive, but it occurs to me that if the above is true, then Win might even be defragging your ext3s and causing those errors. 

Other than that, I dunno. I would guess, however, that if do end up formatting things, you should do that with the FAT32 parts as well, since you indicated the Linux was finding errors on those as well. Since Linux reads those partitions natively, it's kind of hard to completely segregate them. Good luck.

---

