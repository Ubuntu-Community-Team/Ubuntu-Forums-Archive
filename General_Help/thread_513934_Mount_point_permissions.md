---
title: "Mount point permissions"
date: 2007-07-31
forum: General Help
---

### Post by motorollin on 2007-07-31
Please forgive me if this is a really obvious or done-to-death question. I have just set up an Ubuntu 7.04 box as a file server, created a raid 5 array and got it mounted. Initially we were having problems getting access to the Samba share, but then realised that the user we were authenticating as didn't even have local access to the folder.

My entry in fstab was as follows:
/dev/md0 /mnt/raid ext3 defaults 1 2

I then tried changing it to:
/dev/md0 /mnt/raid ext3 rw,users 1 2

and also moving the mount point to /media/raid, but still get permission denied when cd-ing to the directory. The strange thing is that when the drive is mounted in /media/raid an icon appears on the user's desktop for the drive and is read-only, but not read-write (which it needs to be).

I then tried doing this:

# su
# cd /media/raid
# chown <user> .

but still no joy. What am I missing?

TIA
moto

---

### Post by motorollin on 2007-07-31
Ok all sorted. Went in to the permissions of the mount point folder and set them in there. Blx to the command line I say! :p

moto

---

