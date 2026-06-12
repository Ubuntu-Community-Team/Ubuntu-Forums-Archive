---
title: "changing permissions on removable drives"
date: 2008-05-09
forum: General Help
---

### Post by oarking on 2008-05-09
so i made the switch to ubuntu from osx and copied most of my files over (some still in their original directories) to an external. but when i open it up in ubuntu it says i don't have access to those files and i can't change the permissions because i'm not the owner.

i'm sure the workaround is really obvious but i can't put my finger on it. any advice?

---

### Post by vdawg on 2008-05-09
You can make yourself the owner.

sudo chown -R you:yourgroup /mountpoint

or you can change the permissions so that anyone can read/write/execute

sudo chmod -R 777 /mountpoint

/mountpoint is wherever your hdd is mounted, -R switch is for recursively changing permissions/owner in the subdirectories. but you could also do it individually eg.

sudo chmod 777 /mountpoint/folder/file
or
sudo chmod 777 /mountpoint/folder/*

same for chown

---

### Post by oarking on 2008-05-09
hmm, when i do the chmod 777 it says "read-only file system" on every single file and nothing changes...

---

### Post by chrisccoulson on 2008-05-09
If it is a FAT or NTFS volume, then you can't chmod or chown the mounted volume to change the permissions as they have no concept of POSIX file permissions. The permissions and ownership are determined by mount options, and these are what you need to change.

If it tells you that the filesystem is read-only, then it has been mounted read only. It isn't normally because you haven't got write privileges. This could either be due to the 'ro' option being specified at mount time, or the filesystem having errors on it.

What filesystem are you trying to mount, and how are you mounting it? Is it being automounted or is it specified in your /etc/fstab? 

Could you do
```
tail -f /var/log/syslog
```
..in a terminal, then connect your external drive, monitor and post the output here

---

### Post by oarking on 2008-05-09
[I]May  9 09:25:24 syrh-desktop kernel: [ 3927.299318] hfs: write access to a jounaled filesystem is not supported, use the force option at your own risk, mounting read-only.
May  9 09:25:24 syrh-desktop hald: mounted /dev/sdb3 on behalf of uid 1000
[/I]

it's an hfs journaled drive. it still has osx 10.4 installed on it. and i'm just going up to "places" and automounting it. i'm still not comfortable in terminal to just try out commands without advice.

---

### Post by chrisccoulson on 2008-05-09
The error message seems to suggest it has a problem with the journal. I've no experience with HFS, but a quick search on Google brings up this: [http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

Use at your own risk though

---

### Post by oarking on 2008-05-10
the only workaround i can find is plugging it into a mac and using the shell on there to disable journaling then mount it in ubuntu.

anyone else have any ideas?

---

