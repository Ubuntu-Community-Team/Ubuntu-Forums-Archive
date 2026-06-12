---
title: "Wubi no longer loads, system stuck in restart cycle"
date: 2007-06-08
forum: General Help
---

### Post by kevinmedina on 2007-06-08
I've been successfully using Ubuntu a la Wubi for a week now, and have had not a single bad experience with Ubuntu until a few hours ago.  After installing a number of apps on Ubuntu, I restarted my machine.  I see the Dell splash screen and then, when it would typically show me the boot screen, the computer restarts!!! It will continue to restart forever.  I ran Dell diagnostics (pressing F12) and tested all my bootup procedures, but the report passed with flying colors!  I am now stuck with a machine that will not load any OS :-( Please help me! I want to rid my life of M$ and have fallen in love with Ubuntu, I don't want to let this get in the way of my freedom :frown:

My specs:

Dell XPS M140
60 GB HD
1 GB SDRAM
MS XP MCE
Ubuntu FF

---

### Post by ago on 2007-06-08
That means that mbr/partition table/ntfs folder are  not accessible. Boot from a live CD, or use windows cd to check the fs and fix the mbr.

---

### Post by kevinmedina on 2007-06-08
But i thought that Wubi doesn't edit the MBR?  However, this is precisely what I thought....

I recently burned a Linux repair ISO, will this work on a Wubi based  linux install as well?

---

### Post by ago on 2007-06-08
> **kevinmedina said:**
> But i thought that Wubi doesn't edit the MBR?  However, this is precisely what I thought....
In fact it doesn't. There are many reasons why that might happen which have nothing to do with wubi. Sometimes hard reboots cause that too. There are lots of windows-only users with such issues.

> I recently burned a Linux repair ISO, will this work on a Wubi based  linux install as well?
A live ISO will give you raw disk access from linux. Then you need to understand where the problem lies, it can be the MBR/partition table or it can be ntfs corruption, then you have to use the appropriate tools. You can first try to repair it with the windows recovery console.

---

