---
title: "Whole volume has changed ownership to Root"
date: 2007-01-05
forum: General Help
---

### Post by Edward The Bonobo on 2007-01-05
For reasons unknown to me, an entire volume seems to have suddenly changed owner to Root.

I'm not the sort of user who usually changes file permissions or who logs on as Root.  All I know is that I suddenly lost write access to an entire hard drive.  It's a physically separate internal drive, formatted as FAT32.

The first symptom I saw was when I couldn't continue a bittorrent session.  My whole drive - and all subfolders and files - are showing as Owner = Root, Groups = Root (when I do RightClick, Permissions).  Obviously I can't change permissions becaise my user log on is no longer the owner.

Any idea what's happened?  Or - more importantly - what's the easiest way to give myself back permissions for the drive?

Thanks.

---

### Post by tomski on 2007-01-05
Before doing this i would find out if the drive has failed in some way, which may have been caused by bit torrent allocating space for a file that is bigger than the largest file size a fat32 drive/partition can take which i think is 1GB 
so run checks first & make sure the physical drive is ok i would use a Hirens boot cd to check this get it here:

[http://files.9down.com:8080/HBootCD.8.5.rar](http://files.9down.com:8080/HBootCD.8.5.rar)

UnRAR Password: [www.9down.com](www.9down.com)

If all is ok after using the tools on the CD then continue

create root user:

sudo passwd

it will then ask for new unix password provide it with one
then in terminal type:

su

it will ask for password so feed it the one you just created

now you need to get to the volume mount point

then type:
chown -r /path to volume

this is a very basic way of doing it but it may help if all else on the boot cd has failed

---

### Post by bettlebrox on 2007-01-05
How are U mounting the filesystem? Can you show the relevant lines from /etc/fstab?

---

### Post by Edward The Bonobo on 2007-01-08
This turned out to be an example of one of those times when my Linux vocabulary wasn't up to decribing the problem...and googling misled me.

On the separate drive, all files on it are owned by Root by default. but with Others given read/write access.  What had happned - I still don't know why, but never mind - was that 'Others' lost their privileges.  The problem was solved by logging on as root and re-granting privileges.  So...now I've learned how to do that.  And I've learned a bit more about Ownership.

The original problem is still a mystery, but I won't bother investigating...unless it happens again!

---

