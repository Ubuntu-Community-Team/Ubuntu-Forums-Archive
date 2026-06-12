---
title: "Ubuntu WinXP -&gt; 1 Thunderbird"
date: 2008-06-27
forum: General Help
---

### Post by ubunoob2 on 2008-06-27
Hi,
i have currently two OS on my PC. Win XP and Ubuntu 8.
I would like to be able to use Thunderbird from both OS.
I read some Tutorials and found a solution which involved a third partition in FAT32.
My question is: Is it still necessary to have this third partition, since Ubuntu is now appearantly fully capable of reading and writing on the win partition? Are there still any risks to destroy my win partition?
And if i would create a third partition, could it also be a NTFS?
I have these two OS installed since last year and i would prefer not to create a new partition on a running system.
Thanks

---

### Post by schwascore on 2008-06-27
The easiest way to have both Thunderbird applications view the same data is to simply use the IMAP mail protocol rather than POP.  IMAP does not download the mail off of the server to your computer, so you can view it from any client on any computer.  You can still download copies of your mail if you would like, but in the event of a crash/bad upgrade/etc. your data is still on your mail server.

What you are asking is probably possible, but not the most simple solution.

---

### Post by crossedout on 2008-06-28
> I would like to be able to use Thunderbird from both OS.
I read some Tutorials and found a solution which involved a third partition in FAT32.
My question is: Is it still necessary to have this third partition, since Ubuntu is now appearantly fully capable of reading and writing on the win partition?
Using a FAT32 partition for sharing a TB profile between Ubuntu and XP is definitely possible.  The most difficult part is simply creating the partition.
> And if i would create a third partition, could it also be a NTFS?
As far as using NTFS vs FAT32 for sharing, the FAT32 is more stable.  Not to say that NTFS can't be used but occasionally an odd issue can pop up where as FAT32 is time tested.
> Are there still any risks to destroy my win partition?
The actual sharing of the TB profile will not damage your XP partition.

-Xout

---

### Post by nick_h on 2008-06-28
> My question is: Is it still necessary to have this third partition, since Ubuntu is now appearantly fully capable of reading and writing on the win partition?
No, because Ubuntu can read and write to an NTFS partition this is no longer necessary.

> And if i would create a third partition, could it also be a NTFS?
Yes.

> Are there still any risks to destroy my win partition?
Write access to NTFS has been in Ubuntu for some time now.  The risks should be very low.

---

