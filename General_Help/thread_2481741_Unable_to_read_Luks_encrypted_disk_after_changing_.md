---
title: "Unable to read Luks encrypted disk after changing the USB to SATA adapter"
date: 2022-12-08
forum: General Help
---

### Post by ramesh-chandr on 2022-12-08
Hi All, 

I have an encrypted 2.5" internal SATA disk. Which I was  using as a backup through a USB 3.0 to SATA Adapter. For the last week,  I have to get an issue with my USB to SATA Adapter. My disk gets  frequently disconnecting from my laptop. Because of this, I am not able  to use the disk.
So, I thought of using the USB to SATA adapter of my  portable Seagate disk. I opened the portable disk and tried to use it  with my encrypted disk. But I am getting errors while mounting it. See the screenshot of the error below.

[IMG]https://i.imgur.com/2mNWeoL.png[/IMG]

I am sure it is due to the different (type of) USB to SATA adapters. This should not be the case, it should not depend on external hardware. The disk is encrypted and I have topasscode. 

Could anybody let me know how to fix this issue?

Regards
Ramesh chandra

---

### Post by TheFu on 2022-12-08
> **ramesh-chandr said:**
>  
I am sure it is due to the different (type of) USB to SATA adapters. This should not be the case, it should not depend on external hardware. The disk is encrypted and I have topasscode. 

Could anybody let me know how to fix this issue?


I'd guess that the HW failures corrupted the encryption, not any hardware swap.  
How good are your backups? 
Hopefully, you have 3 copies, on 2 different types of media and 1 of those is 500kms away.  That's the 3-2-1 backup requirements.  
Whenever using encryption, excellent backups are mandatory.  Just a few bits in the wrong place and we are locked out, completely. That's the great thing and terrible thing about using good encryption.

A bad superblock isn't good.  [https://unix.stackexchange.com/questions/646569/superblock-problem-on-a-crypto-luks-drive](https://unix.stackexchange.com/questions/646569/superblock-problem-on-a-crypto-luks-drive) has some hints.  Be 100% certain you know which device is inside the LUKS container and you deal with that correctly.  It could be a file system or one of 3+ different volume managers.  If you aren't certain, stop BEFORE running commands that could corrupt the layout even more.

After unlocking the LUKS container, run 'lsblk' with relevant options to see any volume managers or file systems.  After seeing what you have, then you can take the needed steps. If you are stuck, post the lsblk output that includes the file system type within forum code tags to get more help.

If you use the command line to unlock the encrypted storage container, then you might see more information.  'sudo cryptsetup open ....  ' is the start of the command. Then you'll need to mount the storage file system that is inside the LUKS container.  I'd use the 'sudo mount ... ' command.

While doing each of these steps, be certain to watch the logs concurrently, so see if they show any warnings or errors.  Those could confirm my belief OR confirm your belief.  No way to know until the attempts are made.

---

### Post by ramesh-chandr on 2022-12-11
Thanks for replying. 
I bought another USB to SATA adapter. Which is working fine and I am able to access all my files from the encrypted disk. 

I  think Seagate uses some proprietary technology to access disks. That  might be the reason, I was not able to use my encrypted disk using  the Seagate adapter. 

Anyway, I am able to resolve the issue by using another SATA adapter.  Thank you TheFu for helping 

Regards
Ramesh Chandra

---

### Post by TheFu on 2022-12-11
If this is SOLVED, please use the Thread Tools link at the top of the page to mark it so. This helps save time for people seeking answers AND for people wanting to help, so they don't waste their time reading the thread only to discover it is solved.

---

