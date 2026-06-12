---
title: "Ubuntu 14 wiped out after Windows 8.1 update"
date: 2014-09-11
forum: General Help
---

### Post by jeronimozc on 2014-09-11
Hello community,

After I updated Windows 8 to 8.1 I was unable to access Ubuntu. I had been running both OS reasonably well together for a while.
After I returned my boot settings back to how they were (Secure Mode Off), there was an "ubuntu" option to boot, but it tells me there is no filesystem and enters grub rescue mode. The partition were Ubuntu is supposed to be says its "77.77 GB RAW".

Is there anything I can do to get my beloved Ubuntu back, or at least the files it had?
What info should I supply?

---

### Post by michael_1234 on 2014-09-11
Can you boot from cd-rom (or USB) and see if the file system can be mounted, and files backed-up? E.g., [www.sysresccd.org](www.sysresccd.org) since it has various useful tools for the task, or  even from an Ubuntu on USB...

---

### Post by oldfred on 2014-09-12
RAW in Windows means unformatted or missing NTFS signature. But Linux partitions are not NTFS and usually just are not shown at all.
If Windows 8 now shows it I would expect it to see it as RAW as no Linux partition will have a NTFS signature. 

Windows often messes with partition table or partitions that it does not correctly see. It often deletes Linux partitions from partition table (can be restored) with MBR partitioning, not sure with gpt if it still does nasty things.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

