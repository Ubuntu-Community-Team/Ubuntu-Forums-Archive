---
title: "Is gparted &quot;Format to&quot; a destructive format?"
date: 2007-03-11
forum: General Help
---

### Post by knuno on 2007-03-11
I have accidentally made my NTFS boot partition into a Linux swap partition. I have been advices to retag it as a NTFS partition. But how do I do this. "Format to" is the only command that let me set type of partition, but will this command actually format the partition and destroy data, or will it only change partition type?

Knut

---

### Post by OffHand on 2007-03-11
> **knuno said:**
> I have accidentally made my NTFS boot partition into a Linux swap partition. I have been advices to retag it as a NTFS partition. But how do I do this. "Format to" is the only command that let me set type of partition, but will this command actually format the partition and destroy data, or will it only change partition type?

Knut

Did you already format the ntfs partition or have you just set the mount points?

---

### Post by knuno on 2007-03-11
The partition is formatted as a NTFS partition and has worked OK for about a year until I made this stupid error. FDISK recognizes it as a NTFS partition. But gparted says it is a Linux swap partition, and I expect it to be after what I did. I am now unable to boot Windows. So my question is: Can I restore it as the original Windows boot partition by using gparted "Format to" and choosing NTFS without destroying the data on it?

Knut

---

### Post by Lord Illidan on 2007-03-11
No, I doubt you can. Formatting doesn't mean changing a simple tag or too. It means re-arranging sectors and stuff. (wikipedia it for more info).

Did you take backups?

---

### Post by knuno on 2007-03-11
I can recover most of my Windows data, they are on another disk. But it will take me a day or two to restore my Windows system reinstalling programs and upgrades. And I would like to avoid that. I have got the advice to "retag the partition using gparted", I just wanted to know how I do that. Hoping to save a lot of work.

Knut

---

### Post by RogerEvans on 2007-03-11
Hi
I'm a complete newbie here too (my first post...) and I'm in a similar mess. I think the gparted command you want is 'mkpart' (not to be confused with 'mkpartfs', which will erase your data). Use 'print' to find out the start and end specifiers for the partition and then use mkpart to change its file system type. The documentation says this won't affect your actual data at all, so if it doesn't work you shouldn't have lost anything.

(Sadly this doesn't work for me - I think the ubuntu partitioner actually corrupted my file system, so just changing the file system type isn't enough -  if anyone reading this can help me out of *that* mess I'd be very grateful)

Roger

---

### Post by dcstar on 2007-03-11
> **RogerEvans said:**
> Hi
I'm a complete newbie here too (my first post...) and I'm in a similar mess. I think the gparted command you want is 'mkpart' (not to be confused with 'mkpartfs', which will erase your data). Use 'print' to find out the start and end specifiers for the partition and then use mkpart to change its file system type. The documentation says this won't affect your actual data at all, so if it doesn't work you shouldn't have lost anything.

(Sadly this doesn't work for me - I think the ubuntu partitioner actually corrupted my file system, so just changing the file system type isn't enough -  if anyone reading this can help me out of *that* mess I'd be very grateful)

Roger
**cfdisk** is a reasonably usable utility to change a partition type - although I'm not sure of the consequences on existing data.

You should try to run a fsck on the partition after changing it back (or some Windows disk check/repair utility).

---

