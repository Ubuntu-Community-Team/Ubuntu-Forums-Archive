---
title: "Partition Help and GRUB error 17"
date: 2008-03-10
forum: General Help
---

### Post by NewwWorlddOrder on 2008-03-10
So about six to seven months ago I began using ubuntu on my laptop and loved it.  I wouldn't call myself a total linux noob but I wouldn't consider myself seasoned either.  Anyway I dual boot with GRUB 1.5 and have my hard disk partitioned between XP and ubuntu.  

Soooo... a few days ago i deleted(supposedly) my ubuntu partition from within windows because i was planning on installing kubuntu or xubuntu instead.  However, I mistakenly only deleted the files, info, etc. off the partition, not the partition itself.  So now when I attempt to boot the computer is attempting to read the unallocated partition and popping up with a GRUB error 17 message.  

My question now is, basically, what to do now.  The computer freezes and refuses to boot now and I am unable to do anything except enter BIOS.  Should i boot into XP from a disc? would this even work? and if not what to do now?

Thanks, i need all the help I can get

---

### Post by logos34 on 2008-03-10
yep, run fixmbr command from recovery console on xp disc

---

### Post by NewwWorlddOrder on 2008-03-10
Thanks my only problem now is finding an xp recovery disc.  Also, I have a tablet pc, and it runs xp tablet edition.  Do you happen to know if a regular xp disc will be compatible?

---

### Post by but2002 on 2008-03-10
Any XP install CD will work, as long as you have access to fix MBR

The command for a Vista disk is  bootrec /fixmbr   I'm sure it's similar, if not the same on XP

---

### Post by logos34 on 2008-03-10
> **NewwWorlddOrder said:**
> regular xp disc will be compatible?

that's what I meant.  Just press 'R' for the console

---

