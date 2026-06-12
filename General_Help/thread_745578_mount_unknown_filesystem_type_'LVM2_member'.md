---
title: "mount: unknown filesystem type 'LVM2_member'"
date: 2008-04-04
forum: General Help
---

### Post by fritz276 on 2008-04-04
Hi,

I've searched here and on Google, but I dont know what else to try:

I've a crypted partition /dev/sdb1 which I created under a different distribution. I dont remember what steps I followed to create that partition.

I used to mount it like this:

cryptsetup luksOpen /dev/sdb1 media
mount -o user_xattr /dev/mapper/media /mnt/media

Unfortunately, I'm getting:
mount: unknown filesystem type 'LVM2_member'

(I dont even remember if I uses LVM in any steps when creating that partition).

Gparted shows me /dev/mapper/media as reiserfs partition (which is true).
I can reiserfsck /dev/mapper/media without any problems (and I see my filenames and directories with reiserfsck comes to Checking Semantic tree) ?!?!?!

But I cant mount it ?!

I have no idea if the informtaion following now is needed, but I read that in lots of threads.

pvscan:
PV /dev/mapper/media   VG vg   lvm2 [390.62 GB / 390.62 GB free]
Total: 1 [390.62 GB] / in use: 1 [390.62 GB] / in no VG: 0 [0   ]

vgscan:
Reading all physical volumes.  This may take a while...
Found volume group "vg" using metadata type lvm2

lvscan:
(nothing)

lvs:
(nothing)

pvs:
PV                VG   Fmt  Attr PSize   PFree  
/dev/mapper/media vg   lvm2 a-   390.62G 390.62G 

vgs:
VG   #PV #LV #SN Attr   VSize   VFree  
vg     1   0   0 wz--n- 390.62G 390.62G

---

### Post by fritz276 on 2008-04-27
bump.

---

