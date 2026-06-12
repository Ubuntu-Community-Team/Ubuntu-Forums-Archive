---
title: "fitting a Maxtor SATA hard drive"
date: 2008-03-13
forum: General Help
---

### Post by skeletor16940 on 2008-03-13
Hello everyone,

Would appreciate some help with this.  My set-up is 2 hard drives running Windows XP (for wife)and a 3rd hard drive running Ubuntu 7.10 (for me)  I was lucky enough to be given a 160gb hard drive SATA type.  What I would like to do is replace my existing 3rd drive (ubuntu) and replace it with this 160gb drive.  Now the tricky part:-  how can I transfer all my data on the ubuntu drive to my new one?  When I boot up I get the Ubuntu splash screen  asking me which o/s would I like to boot to as obviously the boot loader for Ubuntu is on the "C"  drive.  If I remove the Ubuntu drive, will I lose the boot-up sequence?or do I just remove it, get my BIOS to recognise the SATA drive and then re-install Ubuntu. My mobo is enabled for SATA drives, it is an Asrock 4coredual-sATA2 motherboard. I have 1gig of ram and a Intel dual core processor .  Any help would be much appreciated, thanks to all.

---

### Post by justleen on 2008-03-13
the easiest way would 
- shut down, 
- disconnect drive 3 (grub will complain if you boot now)
- connect the new drive
- boot ubuntu install cd, and install on new drive (grub will be reinstalled, and it pickes up windows again)
- once done, shutdown connect old drive 3. this will now be avail as a data disk. any data on it can be copied over to the new disk.

---

