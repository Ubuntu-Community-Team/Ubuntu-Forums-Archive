---
title: "Transfering hard drive to new computer"
date: 2008-02-28
forum: General Help
---

### Post by Kannasu on 2008-02-28
Hello everyone,

I want to get some opinions on the feasibility on this plan to transfer my 500GB hard drive from my Ubuntu machine to my windows machine *WITHOUT LOSING ANY DATA.*  This hard drive is currently partitioned into 2 NTFS partitions each 250GB.  I have 200GB total being taken up on the hard drive.

I want to move this hard drive into the new computer and I need to figure out the easiest way to do it.  The computer I'm transferring to also has a 500GB hard drive and I do have Samba set-up to transfer files between the two computers.  However I want to also physically move the hard drive into the new computer as well.

Is it possible to move all my files into one of the partitions, bring it into Windows and format the empty partition.  Use a LiveCD to move the files to the newly formated partition, then format the other partition on Windows again?  It seems like it should work :confused:  I never actually tried this befor and it seems like it would go faster than transferring 200GB over my network.

Anyone have some insight on this? Thank you!!

---

### Post by vpjr on 2008-02-28
The new harddrive is added as a SLAVE to the orignally installed harddrive? The originally installed harddrive is a Windows?

---

### Post by Kannasu on 2008-02-28
These are both SATA drives.  Unless I'm mistaken aren't jumper settings different from ATA HDD?

---

### Post by Therion on 2008-02-28
> **Kannasu said:**
> These are both SATA drives.  Unless I'm mistaken aren't jumper settings different from ATA HDD?
Since both drives are SATA, you won't be dealing with jumpers.  

Install the secondary drive and configure the drive settings via the BIOS.

---

### Post by Kannasu on 2008-02-28
Would windows want me to format the second drive?  It was originally from an older windows computer, and I never formatted it after I moved into windows.  If it wants me to format my drives will my little shifting files between partitions work?

---

### Post by Therion on 2008-02-28
I'm under the impression the drive you want to move has already been formatted in NTFS.  If this is the case, I don't see why you couldn't simply install it on the new PC as is, configure the BIOS, and then effect your file transfers.  I'm no expert on Samba, though, so I'm not giving advice in that arena.  

In any case formatting, or re-formatting, a drive will totally wipe any and all data resident ON that drive and that would very much put an end to your little transfer of data plan.  I'm sure you know that since it appears you've managed to format and partition in the past, but your post left me wondering a little, so I just thought I'd point that out.  :)

---

### Post by Kannasu on 2008-02-28
I ask about reformatting after I transfer it to windows because in the past windows has forced me to reformat drives before it will be able to use them.  Even if the drive was originally used in another windows machine It would have to be reformated before being able to actually use it

---

### Post by Therion on 2008-02-28
If the drive is in fact formatted using NTFS, there is no reason Windows should be asking you to reformat the drive before it's willing to access it.  If it does ask if you want to reformat, the answer is "NO".  I would also be at a loss at to tell you what to do next in that case, so hopefully it won't happen.  You should be able to simply install the drive as a slave device and get on with Life as you understand it...  Of course, this IS Windows we're discussing so... 

Good luck and God's speed.

---

