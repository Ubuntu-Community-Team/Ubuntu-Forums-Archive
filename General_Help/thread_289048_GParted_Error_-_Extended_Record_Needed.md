---
title: "GParted Error - Extended Record Needed"
date: 2006-10-30
forum: General Help
---

### Post by marx2k on 2006-10-30
Here is the error I am getting from GParted when trying to resize a partition from 88GB NTFS to 57GB NTFS...

Relocating Needed Data...
ERROR: Extended record needed (1216 > 1024), not yet supported!
Please try to free less space.

So, what's the deal here?
This is during the simulation

---

### Post by bigken on 2006-10-30
have you defraged windows :-k

---

### Post by marx2k on 2006-10-30
Defragged? No, I have not. I did a chkdsk, yes. I did not defrag.  I was unaware that that was important when resizing partitions as it did not effect resizing the partitions on any of the other 4 hard drives on this system, just this one it seems.  The hard drive I am trying to partition MAY be very fragged, I must say as it is an Azureus bittorrent download target.  However, I really was unaware that it was important to defrag before reisizing.

Is that what the cryptic error means?

---

### Post by bigken on 2006-10-30
dont realy know what the error means but its worth a shot ;)

have you googled the error ?

---

### Post by marx2k on 2006-11-24
Turns out it WAS needing to be defragged. Good call.

---

### Post by anjin on 2006-12-19
> **bigken said:**
> dont realy know what the error means but its worth a shot ;)

have you googled the error ?

I googled this error, as I am having the same problem, and found this thread.

It does not seem to be a defrag problem per se, but it does seem to be a problem with "unmovable" files near the end of the current NTFS partition.  I've run defrag (again and again and again), and still can't get some of the unmovable files to move.  Apparently, this error tells me that Gparted can't move these files either.

Some of the unmovable files were windows paging (swap) files, and I had to disable virtual memory in XP in order to defrag (and move) those files.  The other files are unknown.  ](*,) 

Any suggestions?

Thanks!

---

### Post by bigken on 2006-12-19
> **anjin said:**
> I googled this error, as I am having the same problem, and found this thread.

It does not seem to be a defrag problem per se, but it does seem to be a problem with "unmovable" files near the end of the current NTFS partition.  I've run defrag (again and again and again), and still can't get some of the unmovable files to move.  Apparently, this error tells me that Gparted can't move these files either.

Some of the unmovable files were windows paging (swap) files, and I had to disable virtual memory in XP in order to defrag (and move) those files.  The other files are unknown.  ](*,) 

Any suggestions?




Thanks!

You might have to uninstall some packages to make room also just delete the paging (swap) files ;)

---

### Post by anjin on 2006-12-19
> **bigken said:**
> You might have to uninstall some packages to make room also just delete the paging (swap) files ;)

Here's the current plan:

-disable virtual memory
-disable "hibernate" (start|control panel|power settings|hibernate)
-defrag
-reboot with Gparted Live CD 
-repartition NTFS

The rest should be pretty simple.  Nowhere on teh intarwebs are the above sequence found, so I figured I'd post it here and maybe save someone hours of frustration!  (assuming it works)

I'll post my results. . .

---

### Post by tek1024 on 2008-01-08
I know it's over a year later, but what indeed were the results of doing so?

---

### Post by fearpi on 2008-03-16
I've been having a similar error. Only difference is that mine concludes with "(1096 > 1024)". I will be doing that last mentioned sequence right now. I'll report back for anyone who's interested.

---

### Post by Ergose on 2008-07-01
Yeah I'd like to hear the results also.
My error is:
Extended record needed (1048>1024),not yet supported.
Please try less free space.

I have seen where the swap and such is towards the end of the drive, but in the past I remember a clue to that was that the color bar, if I remember correctly, it was pretty much full even though the drive wasn't, but what was white could be allocated without bumping the files forward. Now though it looks to be showing about how much is really being used?? I just realized I'm probably being abit confusing... hmm..

Ok, let's say it this way. If I have a white block that is detected as the part that is resizable (in this case shrinkable) then I should not be able to shrink it any more than the colored bar (The span of where written data has been confirmed.) So an error for not going all the way to the colored bar on a shrink from 1  XP NTFS partition to a smaller NTFS and Unallocated Space should not be a problem.

Also the "Please try less free space." part. I can see that may be a clue to defrag anyway, but if that range was to large, then why didn't the colored bar and the dragable resize bar show the same data in the first place. I could have sworn that this used to not be the case because another time I did this I remember it odd that there was only 20?megs of allocatable space on a barely full 30gig drive and was like.. ding "Gotta be the darn swapfile". That was a case where the bar reached almost to the end of the drive.

So by all means, let me know what your results were because my system is very slow and the last time I did something like this it was an extra few hours to remove the swap, defrag etc... I'm low on ram too which doesn't help.

Thank in advance.

---

