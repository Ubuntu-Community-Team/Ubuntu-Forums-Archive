---
title: "Backing up from ext3 to NTFS"
date: 2008-02-20
forum: General Help
---

### Post by SumnerBoy on 2008-02-20
Hi - I am setting up my backup routines using rsync from my ext3 HDD to an NTFS external USB drive. I am using the following rsync command...

rsync -auv /src /dst

I was assuming the -a flag would ensure all permissions and ownerships were copied across but all files/dirs are copied with the root owner/group.

Is this something to do with the fact the external drive is not ext3? What would happen if I needed to restore from my backup? All my permissions would be lost - correct?

---

### Post by bodhi.zazen on 2008-02-20
Yes, I believe permissions would not be "lost", I bet they would be set to the ownership and permissions of the NTFS partition.

Why not make an ext3 or other linux native partition on the drive ?

---

### Post by SumnerBoy on 2008-02-20
I want to keep it NTFS as I often use the drive to transfer photos/music to other peoples Windoze machines.

Does this kinda of diminish the value of my backups? Since there will be all sorts of issues with permissions if I had to do a restore from this backup.

---

### Post by bodhi.zazen on 2008-02-20
Yea, but you can use another tool like tar or partimage.

---

