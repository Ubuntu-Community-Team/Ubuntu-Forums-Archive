---
title: "Cannot boot into windows"
date: 2007-09-14
forum: General Help
---

### Post by unca.paka on 2007-09-14
Hey all, I've searched the forums for about an hour, and could not find a solution to my problem.
Anyway, Ive got a dual boot setup, on different hdd's.

Sata 0 - Windows
Sata 1 - Ubuntu

Everything worked out fine, installation, booting either windows or linux. Not sure what I did, but now windows wont boot, and I cant even mount the drive.

Ive attached a few screenshots of whats happening when I try.
Any help would be appreciated.

---

### Post by rivalarrival on 2007-09-14
It looks like a bad master boot record on sata 0.
Load your windows installation disk, boot to a recovery console, and fixmbr

(You might want to wait for someone else to confirm that before you try it...  I'm not sure if it will toast GRUB.)

---

### Post by unca.paka on 2007-09-14
It should work if I install GRUB onto the linux drive, shouldnt it? That way(how i understand it) I would just have to change the boot order in the BIOS to boot the linux drive 1st.

---

### Post by unca.paka on 2007-09-15
Turns out it was a hashed MBR. Restored it, and windows boots fine.
Problem was, I installed GRUB into the partition itself. Oh well, live and learn.

---

