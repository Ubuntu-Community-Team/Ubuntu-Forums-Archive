---
title: "two /home partitions?"
date: 2008-01-03
forum: General Help
---

### Post by jmblock2 on 2008-01-03
Hi, I am a new linux user.  Ive been reinstalling ubuntu several times now just messing with it and my final setup involves two hard drives.  Each has a gig of swap space and the master is half windows XP and half ubuntu /.  The rest of the slave hard drive is my original /home directory.  I originally installed with the desktop version of ubuntu and everything was fine, but I decided I wanted to do a fresh install after loading a bunch of garbage with the server edition.  So I went through a guide and deleted my / partition from the first hard drive and remade it and reinstalled.  For some reason I have another /home folder and I am having trouble figuring out how to unmount/remount things to get it back to being correct.  Could someone please give me a few pointers on what I need to do?  Thanks for your time.

---

### Post by Jussi Kukkonen on 2008-01-03
You might want to explain the current and wanted situations with even more detail (these things are difficult to understand from text). *sudo fdisk -l* will give you the list of current partitions, *mount* the list of current mounts.

Btw, you won't need two swap partitions.

---

### Post by jmblock2 on 2008-01-03
Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         122      979933+  82  Linux swap / Solaris
/dev/hda2   *         123        5094    39937590    7  HPFS/NTFS
/dev/hda3            5095        9729    37230637+  83  Linux

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         122      979933+  82  Linux swap / Solaris
/dev/hdb2             123       14593   116238307+  83  Linux

hda2 is windows.  hda3 is / and hdb2 is /home

Right now I have a /home also in hda2.  I am not sure why it happened, its just there.  I want that removed and for /home to point to hdb2.

The reason I did two swap files was because I have 2 gigs of memory and I was originally trying out freeBSD and a guide said its better to split if you can.  I will fix that sometime down the road.  Am I being clearer?  Thanks for the help.

---

### Post by jmblock2 on 2008-01-03
bumping the post

---

### Post by chrisccoulson on 2008-01-03
Can you post the contents of your /etc/fstab? What I think has happened is that the install has created a new /home folder on the root filesystem. If I understand correctly, you want your previous /home partition mounted instead.

If this is the case, I would probably drop to single-user mode, rename the new /home folder to something else, create a new /home folder then mount the old partition - something like:

```
sudo init 1
mv /home /home_old
mkdir /home
mount -t ext3 /dev/hdb2 /home

```

Then you'll need to chown your home folder so that you actually own it:
```
cd /home
chown <*user_name*>:<*user_name*> <*user_name*>
```
where <*user_name*> is your username.

Then switch back to multi-user:
```
init 2
```

To make it permanant, you'll need to add a line to your /etc/fstab, something like:
```
/dev/hdb2  /home  ext3  defaults  0  0
```
although, you could replace /dev/hdb2 with the UUID of the partition, which can be found by doing:
```
blkid /dev/hdb2
```
so that the line looks like:
```
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx  /home  ext3  defaults  0  0
```

If there's nothing you want in the /home folder that is on your new install, you could get rid of /home_old

---

### Post by jmblock2 on 2008-01-03
When switching back to multi-user i get the error message after trying to login:

"User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  Fileshould be owned by user and have 644 permissions.  User's $Home directory must be owned by user and not writable by other users.

Could it be that my user shouldn't own the whole /home drive?  Just the user folder in the home drive?  And just for my understanding, why do we make a new /home directory then mount /home from /hdb2?

---

### Post by chrisccoulson on 2008-01-03
The user shouldn't own /home - root should. The user should only own their home folder under /home. The error you see probably means your ~/.dmrc file isn't owned by you and doesn't have 644 permissions. If you can't log in, then you'll need to chown it and chmod it to 644 from the console. Otherwise, just fire up a terminal and do it.

Also make sure that your home folder is only writable by you (I think it should have 755 permissions by default)

In my first post, I should have advised you to do a recursive chown on your home folder - which is probably why it hasnt worked. Try:

```
sudo chown -R <user_name>:<user_name> $HOME
sudo chmod 755 $HOME
chmod 644 $HOME/.dmrc
```
assuming you're logged in as yourself and not root of course. If you're not logged in as yourself, then replace $HOME with the path of your users home folder (/home/<*user_name*>) as before

The reason we created a new /home folder is because the install would have created new user profiles under /home, so we remove them from disk before mounting another filesystem under /home - this means your home partition is mounted in to an empty folder, which is what we want. All we've done is rename the newly existing /home folder (created by the install) so you can restore it if you need to.

If you do a ls -l in /home, you should see something like this:

```
drwxr-xr-x  194 chr1s chr1s 8192 2008-01-03 16:42 chr1s
drwxr-xr-x   77 j0ey  j0ey  4096 2008-01-02 00:31 j0ey
drwx------    2 root  root  4096 2007-04-08 17:30 lost+found
```

Hope that helps :)

---

