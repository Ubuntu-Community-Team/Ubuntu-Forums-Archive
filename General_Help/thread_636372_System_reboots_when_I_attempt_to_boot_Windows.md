---
title: "System reboots when I attempt to boot Windows"
date: 2007-12-09
forum: General Help
---

### Post by hypersoar on 2007-12-09
When I attempt to boot windows, the system reboots back into the boot loader. I tried restoring GRUB from a supergrub disk, I tried restoring the windows loader the same way, and I tried  FIXMBR and FIXBOOT with my windows install disk after setting the windows drive to boot in the BIOS (linux and windows are on separate harddrives). With the loader put in place by fixmbr and fixboot, my computer just does an infinite loop.

Help?

---

### Post by atlfalcons866 on 2007-12-09
do you see a bluescreen at all even for a second before it reboots?

---

### Post by hypersoar on 2007-12-10
No. I saw a blank screen with a cursor, then the monitor turned off briefly and it rebooted.

---

### Post by oodledoodle on 2007-12-10
im not positive, but if its the same problem i had its to do with windows rewriting the master boot record every time it boots. to fix it i installed grub on another drive (not just a seperate partition) but if you havent got another drive spare then i guess its not much help.

---

### Post by chalewa on 2007-12-10
are you sure that grub correctly points to the windows partition?

---

### Post by hypersoar on 2007-12-10
I haven't checked explicitly, but the same bootloader had been working fine for a while. 

GRUB is on a separate harddrive from my windows install. 

I might just partition out the files I need from windows (I can still access them from linux) and reinstall if I can't get this working.

---

