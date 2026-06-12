---
title: "new install, won't boot"
date: 2013-01-03
forum: General Help
---

### Post by de Bacon on 2013-01-03
I just reformatted a HDD, installed UbuntuStudio from dvd, (having checked MD5 and hash prior and ran the dvd check of the live disc before attempting) no errors shown.  The system won't boot.
I have gone back to gparted on the live disc, as well as booting to an installed ubuntu 12.04 (different hdd) and also another install of kubuntu's equivalent KDE Partition Manager (different hdd's) where I ran a check of the hdd, finding no errors, no bad sectors, nothing seems wrong.

When I try to boot to the disc, I guess it is a shell, shows the prompt
Grub Rescue> 

I have looked at all that I can think of.  The OS looks to be in place when looking at the file structure through Nautilus or Dolphin at present.  I actually don't know what files should be where in the structure, thus can't identify any discrepancies in that way.  

Any help would be appreciated.  
thanks

---

### Post by de Bacon on 2013-01-04
I found the page [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting) although it failed to resolve the issue.  I don't know if it is some odd thing different in the OS for Studio, or if it is simply an issue of the install loading process resulting in this problem.  I really don't want to re-format and or re-do the partition on the HDD yet again, though it might come to that?  

Anyhow, as per the instructions in the page above, I had mixed results but never correcting the issue with an actual boot in many tries.  Here is what I did and the results from the section called "grub rescue>" within the above url:
I have checked the hdd for files and their location (all correct), I proceed through the steps, 1 - 5 (eventually) with out problem, restarting the process several times for the sake of repeatability.  

At step 5, grub loaded, though it would not function.  The instructions don't cover what to do if and when grub loads???  So at grub, I selected the OS x.x.x.x and grub then cycled back to the initial stage which prompted this symptom in the first place, grub rescue> (the prompt).  
From that point I re-booted and attempted to circumvent that by doing the following:
when grub loaded, I entered "c" to go back to the command line. This time the message at the command line was different, being simply " grub> ".  From there attempting step 6 resulted in the message, "no such partition" (or some near equivalent statement).  
I went back to the page above and then to the section covering " grub> ".  
The grub.cfg is present in the correct location.  Seems I got lost at that point, but will go back and try again.  That is correct, I needed to get a copy of the instructions for " grub> " before proceeding, got distracted with life and now I have written this.  The distraction centered around reading something at the bottom of the page about the partition types.  
> When your boot partition (the one providing /boot) is a LV, make sure not to have any LVM snapshots inside the containing VG. At reboot this will render your system unbootable, dropping you in a "grub rescue>"-shell with the following message: "error: no such disk."

 There are no clear definitions for the acronyms used in that paragraph. In searching for definitions I found too many conflicting meanings to make any sense of the above statement.  That was my distraction.  Regardless I didn't use logical partitions, so this should not be an issue.  

Still searching for the answer.  I am now copying data from the other partition on the HDD I loaded Ubuntu_Studio on, just for protection.  This secondary also primary partition on the HDD is formated to fat32, which I don't believe can be an issue, though my ignorance abounds.
****edited in*****
By the way, The version of Studio I am dealing with is the 32 bit version rather than the 64 bit due to a different recommendation in the Ubuntu_Studio forum page.

---

### Post by de Bacon on 2013-01-04
I fixed it with no input from the forum.  Thanks for all the help, NOT. 
The resolution was the use of the program boot-repair.  Fixed it well in one try.  It was just getting to that point, guessing what to try next!!

---

