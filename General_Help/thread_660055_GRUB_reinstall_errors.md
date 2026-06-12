---
title: "GRUB reinstall errors"
date: 2008-01-06
forum: General Help
---

### Post by YodaMstr on 2008-01-06
Ok, so, installed Ubuntu from a fresh Vista system.  Everything goes fine, but I can't get the MFT files to move and let me at the 30+ gigs of free space on my Vista partition that I wanted to added to my file partition.  So, I start running low on space in my main file partition and I give up and decide to reinstall Vista on a clean 10gig partition so I can get at the rest of the space.  

Everything goes fine, miffed that it auto-overwrites the MBR, and I get that it installed all proper.  So I boot up into my Ubuntu Live CD and follow the instructions on how to restore GRUB....almost.  Instead of typing "setup (hd0)" I typed "setup (hd0,1)" - the same location that my find command earlier had returned.  I didn't realize this and I restarted my system thinking GRUB would be back and....it wasn't.  So I reread the instructions, saw where I messed up, and tried it again.  Get through it alright, shutdown, and....GRUB doesn't work.  I get Error 17: Can't mount drive, or something to that effect.  It won't even boot my Windows partition, so I'm not entirely sure I corrupted the actual Ubuntu install when I goofed on the GRUB install.

Anyone know a way to fix this?  It'd be greatly appreciated.

The instructions I followed for [reference]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by stzasnail on 2008-01-06
Is your drive a SATA drive? If so, replace HD with SD. that may fix it.

EDIT: Haha. Misspelled SATA.

---

### Post by YodaMstr on 2008-01-06
Thanks for trying, but the find command returns an HD command, and if I try to give it SD, it'll return a parsing error.  Still need help. :\

---

### Post by YodaMstr on 2008-01-06
Bump.  Any help, anyone?  I'm installing Ubuntu again as a last resort, and it's able to recognize that I have an account set up on another Ubuntu partition.  Please, I don't want to lose all my information, settings, and software.

---

