---
title: "Problem with installing Hardy in XP"
date: 2008-06-12
forum: General Help
---

### Post by Brain_of_J on 2008-06-12
I am having an issue with installing Wubi on a fresh XP installation (as in I just formatted the drive and installed XP) on a laptop (i can give the hardware info if that's needed).

Wubi will attempt to install Ubuntu (from a live cd) as it should but will fail out at the end, throwing a windows error...

The error in the Windows Event Viewer states 
"Faulting application wubi.exe, version 8.4.0.495, faulting module unknown, version 0.0.0.0, fault address 0x6f902ae4"

I briefly had Hardy running fine on this laptop but wanted to dual boot so I could use some Windows apps I need for work...

---

### Post by ago on 2008-06-12
there should be a log in your user temp folder. please post it here

---

### Post by Brain_of_J on 2008-06-12
So this is beyond weird.
Yesterday when I attempted to find that log file, I couldn't find it. (after the error appeared I followed the path and couldn't find anything...I also searched for the filename and came up with nada...).

Today, I re-ran the installation and so far everything seems to be going well. 
The Windows portion of the install completed and now it's running through the rest in Ubuntu.

Weird? Yes?

edit:
I spoke too soon apparently.
the file in the Temp\WER14.tmp.dir00\appcompat.txt (referenced in the error message that is produced) does not exist.

---

### Post by T2manner on 2008-06-12
have you checked to see if it is hidden?

---

### Post by Brain_of_J on 2008-06-12
Wow.
Do I feel like a moron...


side note:
is there a way to have it make a 20GB partition instead of just 15 or 30?

---

