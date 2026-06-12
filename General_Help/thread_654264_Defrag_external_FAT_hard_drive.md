---
title: "Defrag external FAT hard drive"
date: 2007-12-30
forum: General Help
---

### Post by timboellis on 2007-12-30
Yes I knwo the answer Linux does nto need a defrag however I have an external HDD that is based on FAT32 however it is FAT32 as I occassionaly use it to tranfer files etc. when fixing peoples computers, so can I defreag it or clean it up somehow

---

### Post by p_quarles on 2007-12-30
I myself have looked for a similar tool, and I've never been able to find anything. The only defrag tools I've found for Linux (ext2/3 *does *fragment -- just very, very slowly) can only be used for *nix type filesystems.

Your best bets are to either use Windows itself for this task (and even something as old an Win 95 will be able to deal with FAT32, and it would take very little HDD space to dual-boot with that), or try one of the third-party defrag tools using Wine or CrossoverOffice.

---

### Post by 37wombats on 2008-01-24
thanks, p_quarles. that's what i did. i dual-booted into i  into windows, deleted stuff and de-fragged the hell out the windows partition several times to free up space. 

i have been using ubuntu for about two hours now. i love it. it's intuitive, it's attractive, and it's functional. linux has improved way lots since the last time i used it, about a year and a half ago. it's going to be fun exploring what this o/s can do.

--dave

---

### Post by y-lee on 2008-01-24
It seems to me  one could use a DOS emulator in ubuntu and run a defrag program for DOS since FAT32 is a DOS File structure. DOS Box is in the repos btw. I dunno never tried it.:lolflag:

---

