---
title: "[SOLVED] QTparted now Vista won't boot"
date: 2008-02-02
forum: General Help
---

### Post by dhysk on 2008-02-02
So I'm dumb.  Apparently qtparted doesn't support Vista, shoulda known when i got the warning message unsupported NTFS file system detected.  Leason learned.

What i did:  resized vista partition with QtParted.  ALeady had a working dual boot just wanted more space given to Linux.

So i ignored the warning, stupid stupid stupid, and now vista wont boot.  I have an HP DV6000 series laptop and neither the restore disks nor the restore partition will work either. Not sure what good they are then....

What I've tired

I had to turn off native support in the bios for SATA so i could use an old XP cd to try to fix the MBR....unfortunately Vista's admin account is disabled so that wont work just tells me tha password is wrong.  So i tried to use NTpassword to unlock the account but it wont mount the partition because of "unknown flags" being set so i cant save the changes to the SAM file.

The other option I've tried is using ntfsprogs but when i try to use

sudo ntfsfix /dev/sda1

I get

ntfsfix: error while loading shared libraries: libntfs.so.10: cannot open shared object file: No such file or directory

And sure enouph it wont load the lib files when i try to do the 

make libs

i get 

configure: WARNING: Linux-NTFS Gnome VFS module requires glib-2.0 and gnome-vfs-module-2.0 libraries.
checking for FUSE... no
configure: WARNING: ntfsmount requires FUSE version >= 2.6.1.
./configure: line 20709: syntax error near unexpected token `1.2.2,'
./configure: line 20709: `      AM_PATH_LIBGCRYPT(1.2.2,  have_libgcrypt=true ,'
make: *** [config.status] Error 2




so anyideas?

---

### Post by dhysk on 2008-02-02
bump

---

### Post by dhysk on 2008-02-03
bump....

well atleast i did something right nobody seams to know what to do.

---

### Post by jrusso2 on 2008-02-03
Sounds like the partitions are messed up so I am thinking you might need to start clean and delete the partitions you have and recreate them.  Then fix the mbr and reinstall vista from a vista cd.

---

### Post by dhysk on 2008-02-03
ya unfortunatly not an option right now. I'd have to buy a Vista CD or try to talk HP into sending me one.  I just can't believe the restor cd's dont work

---

### Post by dhysk on 2008-02-03
Finely got ntfsprogs to work.  Had to install the libgnome-vfs, i figured it would already be there but apparently i was wrong..

After i installed the libgnome-vfs i was able to build the lib files for ntfsprog 

Then i just did

sudo ntfsfix /dev/sda1/

It worked and I was able to use the restore drive to get vista back.

---

