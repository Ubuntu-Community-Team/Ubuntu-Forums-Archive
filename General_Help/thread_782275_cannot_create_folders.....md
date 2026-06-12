---
title: "cannot create folders...."
date: 2008-05-04
forum: General Help
---

### Post by andrewchan619 on 2008-05-04
every i manage to create a folder to arrange my files it always doesn't work, there is always message popping up saying "error while creating directory titled folder" then if you click the show details there is message showing there is no space in the device? what the hell i still have 60 gigabyte of free space... can somebody help me..... please

---

### Post by fjgaude on 2008-05-04
You normally have to be root to create a directory:

sudo mkdir /<dir>/<subdir>

That should work.

Let us know if it doesn't.

---

### Post by JacobSteelsmith on 2008-05-04
If the user is in their home directory, sudo shouldn't be necessary. And the error message regarding being out of space suggests a partition or disk problem. 

@andrew, can you please google/post the exact error mssage and post exactly where you're trying to create a folder?

---

### Post by andrewchan619 on 2008-05-04
uhmmmm sir i am just noob ... how ? errrr.....

---

### Post by andrewchan619 on 2008-05-04
@jacob

here is the message sir "Error while creating directory untitled folder"
at the bottom of the message "There was an error creating the directory in /home/andrew."
 at the show more details "Error removing file: No space left on device"

---

### Post by JacobSteelsmith on 2008-05-04
Can you please start a terminal (Applications -> Accessories -> Terminal) and post the output you get after typing "df -h" at the command prompt?

---

### Post by andrewchan619 on 2008-05-04
sir here is the thing comes out 
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      3.7G  558M  3.0G  16% /
varrun                505M  104K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   60K  505M   1% /dev
devshm                505M  136K  505M   1% /dev/shm
lrm                   505M   38M  468M   8% /lib/modules/2.6.24-16-generic/volatile
/host/ubuntu/disks/home.disk
                      3.7G  1.7G  1.9G  49% /home
/host/ubuntu/disks/usr.disk
                      3.7G  2.0G  1.6G  56% /usr
gvfs-fuse-daemon      3.7G  558M  3.0G  16% /home/andrew/.gvfs
/dev/sdb1             7.7G  289M  7.4G   4% /media/disk
/dev/scd0             4.4G  4.4G     0 100% /media/cdrom0
/dev/sda2              54G   38G   16G  72% /media/disk-1

---

