---
title: "Dual boot failure recovery"
date: 2020-10-05
forum: General Help
---

### Post by helen314 on 2020-10-05
I need some assistance to recover from (dual boot) OS failure.  
 My primary concern is NOT to loose ANY data , period.  
 
 
 Up front - this is NOT simple Yes / No  question , hence   here is some background.  

 
 
 I had working  muti-boot Ubuntu 16.04 system with an array of hard drive disks , both SATA  and USB.  

 My data disks are in several RAID5 arrays. - primary to keep my data safe.   
 I have been successfully alternating between TWO perfectly working “boot systems” (via grub) UNTIL I  needed to activate UNUSED RAID5 array.  

 
 
 For yet unknown reason my primary OS now boots ONLY to “emergency mode” and so far I am unable to recover from this mode back to normal boot.  
 
 
 My inability to use my primary OS demonstrated itself  as some kinda of “frozen”  option boot printout which was stuck in an endless loop.  

 From this I did identify possible issue with the RAID I was working with – so I physically removed ONE of the RAID disks.  
 The “endless loops “ went away.  
 
 
 
 
 I have been going thru “grub”  “advanced boot” - without much success.
 I have several versions of “recovery”, but they  always end in “emergency boot mode” 

 
 
 It looks as “emergency recovery “  is very unreliable - simple text menu does not always  return same keyboard entries.  

 
 
 Since I still have ONE perfectly working OS version I was thinking about configuring my system so I can have access to the broken OS files. ( My working OS unfortunately has no direct access to data I need )  

I did try Ubuntu GUI "add user" and it was a disaster - you can add user without password , but you need his password to delete him! 
You can choose activate without password  , but you still need a password to use CLI. 
And when you use passwrod - it has to meet  UBUNTU/ Linux criteria ! 

 
 
 [B]I  asked Mrs Google  but got nowhere.  
[/B]
**I think I need to add “group” and then have users from each OS added to such group. **
**Is that feasible?  **

Any other suggestions, preferably CLI would be welcome. 

Please keep in mind - I need to keep the existing data - and since I cannot access the OS I cannot do backup! 

I would;d not mind installing fresh / clean  Ubuntu and then add the "group". Disk space is of no issue.

---

