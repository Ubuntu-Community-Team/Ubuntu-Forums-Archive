---
title: "Create a mount point on new partition as /home"
date: 2015-06-10
forum: General Help
---

### Post by bookie2 on 2015-06-10
Hi guys!

I installed Ubuntu in VMWare Works Station and because of the limitations for space on my server the drive space was 60GB...

I let Ubuntu use the whole space when installing...

I cloned the vm with clonezilla and moved it to a laptop with a broken screen....the laptop has a 320GB drive and I have created a new partition to cover the rest of the drive...

When I looked in fstab I just see swap and /...

Am I right in assuming I can create a mount point as /home for the rest of the drive?

bookie32

---

### Post by nerdtron on 2015-06-10
Yes indeed.  But I rather not mount it as /home.

BTW, did you already format the extra partition? Can you already mount it and save files on it? I assume the mount point is on /media/XXXXXX/ right?

---

### Post by bookie2 on 2015-06-11
Hi nerdtron:p
No, the drive isn't mounted...just formated it...
But, as you said, I wont mount it to /home/user....rather /home/user/Backup
At least it is visible via cairo-dock...
Thanks!
bookie2

---

