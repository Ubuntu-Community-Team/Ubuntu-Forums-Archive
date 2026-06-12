---
title: "Add SSD, clone linux partition questions"
date: 2014-09-08
forum: General Help
---

### Post by drfox on 2014-09-08
I need some direction. I currently have a dual-boot notebook with a 1TB HD. It has Win 8.1 and no matter what I've tried, I can't get it to default boot into linux. 
I thought I might add a 2nd drive--I have a spare 250GB SSD, and I would like to clone my linux setup, mostly boot from that drive, and only boot from the 2nd drive if absolutely necessary to use windows. 
My /home directory is larger than 250GB,  so I would have to move some data (maybe photos) to a different partition other than /home if I wanted to transfer most of my /home to the SSD.
How do I go about cloning the linux portion to a smaller drive, and how do I prevent Win 8.1 from taking over the boot process?
Thank you.

---

### Post by TheFu on 2014-09-08
**fsarchive** can migrate at a partition level - you'll need to manually handle the UUID changes inside the fstab and booting. This assumes the new storage can actually hold the data. If it won't fit - delete some stuff first.

For the booting - google "ubuntu uefi" - read that result carefully. There's a section a ways down about migrating.

---

