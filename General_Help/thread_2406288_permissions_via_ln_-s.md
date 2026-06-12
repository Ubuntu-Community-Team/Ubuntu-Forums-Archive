---
title: "permissions via ln -s"
date: 2018-11-18
forum: General Help
---

### Post by aeronutt on 2018-11-18
I have a directory, ABC, that I can delete files from via Nautilus and it puts them in the Trash.
I have a soft link to that same directory, ABC, that when I navigate to ABC through the soft link with Nautilus, I must 'delete permanently', and cannot delete to Trash.

ls -l from the directory containing the soft link to ABC
lrwxrwxrwx 1 user1 user1   41 Nov 16 09:12 ABC -> /mnt/Files/ABC/

ls -l from directory containing ABC
drwxr-xr-x 2 user1 user1 4096 Nov 18 15:20 ABC

Seems like a permissions issue, but I can't see what's up?

---

### Post by TheFu on 2018-11-18
Trash is available on a per partition basis.  Symbolic links can cross partition boundaries, which appears to be the situation above. The symlink points to a partition on a different physical disk.

BTW, everywhere I wrote "partition" could easily have been "logical volume."  For almost everything outside administrative tasks, those terms are interchangeable.  LVs are available when LVM is being used for storage management.

Anyway, that's why it doesn't work.

---

### Post by aeronutt on 2018-11-19
Well, that makes sense, BUT.....

There's a 3rd partition that if I link to, delete->Trash works as I'd like.
Also, I have several OS's that I boot. Under 18.10, the above as described happens. Under 18.04, delete->Trash works as I"d like.

So, there's something going on other than the fact that it's simply on another partition.

---

### Post by TheFu on 2018-11-19
I don't use a GUI for file management and have a Trash deletion for all userids at the start of my daily backup scripts, but I've been using Unix OSes for 25+ yrs.

Is there sufficient storage to hold all the deleted files in your HOME, where the trash directory would be located?

Also, perhaps the version of gnome gio/gvfs libraries behave differently in the different releases?

Just throwing out some more guesses.

---

### Post by aeronutt on 2018-11-19
> **TheFu said:**
> I don't use a GUI for file management and have a Trash deletion for all userids at the start of my daily backup scripts, but I've been using Unix OSes for 25+ yrs.

Is there sufficient storage to hold all the deleted files in your HOME, where the trash directory would be located?

Also, perhaps the version of gnome gio/gvfs libraries behave differently in the different releases?

Just throwing out some more guesses.

Good ideas...
1) df -h .  reveals 19G of free space in HOME. And the files I'm trying to delete are a few KB.

2) The odd thing is it behaves differently in the same release (18.10) depending on the partition.

---

### Post by TheFu on 2018-11-19
Which file systems are involved? Could that be the difference?

---

### Post by aeronutt on 2018-11-19
> **TheFu said:**
> Which file systems are involved? Could that be the difference?

Ding Ding! Ok, this question made me think...
The partition I'm having this 'problem' with is a veracrypt partition. (I decrypt it via a veracrypt command in .profile.)

BUT, as I understand it, a difference between 18.04 and 18.10 is that gnome-disks (aka disks) 'understands' veracrypt partitions in 18.10. I have researched, and don't know what that really means.

Using 'disks' to look at the partition in both 18.04 and 18.10, they look the same, except the 'used' space is slightly different. FYI, this veracrypt partition is setup as ext4.

---

### Post by aeronutt on 2018-11-20
UPDATE: Loaded Nemo on Ubuntu 18.10, and it works as I'd expect. When navigating to directories via a soft link, I can 'delete to Trash' using Nemo. Cannot with Nautilus.

I still think this might have something to do with gnome-disks and veracrypt, because when I use Nautilus to navigate to another non-veracrypt partition via softlink, it works find.

Strange.
Worth a bug report to Nautilus?

---

### Post by aeronutt on 2018-11-20
Turns out it was a bug. Was fixed a few weeks ago, and should be backported into stable branch and available soon. 
Marked solved.

---

