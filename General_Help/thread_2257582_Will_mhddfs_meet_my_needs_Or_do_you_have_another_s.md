---
title: "Will mhddfs meet my needs? Or do you have another suggestion?"
date: 2014-12-20
forum: General Help
---

### Post by YQ002lc2 on 2014-12-20
I have multiple HDDs ranging in size from 30 GB to 3 TB. The majority of them are currently filled to the brim.

I will be adding new drives from time to time and want some type of volume management to make the organizational and backup process simpler.

I currently connect all the drives to to a desktop server which I connect to through ssh.

I read about mhddfs and wonder if it can meet my use requirements below.

Requirements: I'm looking for a solution that will keep logs of how it has written data. For instance, let's say that I write a file that (for space reasons) must be spanned across 5 drives in my virtual file system. I want a log file that says something like File1_in_VirtualDirectoryXYZ=={bits 1-50=>Drive1_sectors, bits 50-2000=>Drive2_sectors...}. I would keep multiple updated copies of this log file. Then, if the software fails, I can reinstall it and use this log file to accurately interpret the extant data. If one drive fails, only the portion of data that was spanned on that drive would be lost.

And I would want the program to always try to keep files contiguous. For instance, if I add a new drive to my virtual system, the file that was spanned across 5 drives would be moved to the new drive to keep it contiguous.

Temporary backups would be nice, as well. Let me explain. Lets say I have 4/6 TB used in my array used and I want to backup 2 TB of my data, it will backup the data I select and delete it as I fill up the array. It will tell me each time it deletes the backup copy.

And if one drive fails and the backup contains the missing data, it would then be treated as the original data.

I don't like what I've read about LVM and RAID because it seems that you could lose the ability to interpret your data if the software gets fouled up. I will always keep the most essential pieces of information backed up in case it all fails, but I don't always have the money for extra backup drives. So I take risks with less essential data. It would be nice to have some kind of data integrity and loss-prevention paradigms built-in as I described above.

Honestly, I was considering a ZFS Raid, but I don't have the money to buy a powerful enough computer to handle the deduplication.... I would want.

Any suggestions or information are greatly appreciated.

Thank you!

Tags: mhddfs lvm raid zfsraid jbod lubuntu fluxbox grsync sshserver


See also:
[http://askubuntu.com/questions/563815/will-mhddfs-meet-my-needs-or-do-you-have-another-suggestion](http://askubuntu.com/questions/563815/will-mhddfs-meet-my-needs-or-do-you-have-another-suggestion)

---

