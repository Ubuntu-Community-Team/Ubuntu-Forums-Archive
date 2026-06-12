---
title: "Deleted Items not appearing in Trash folder.  Stuck in .TRASH-1000"
date: 2014-10-14
forum: General Help
---

### Post by sir-marky on 2014-10-14
I have a three 3TB discs in a BTRFS RAID 1 configuration mounted at [FONT=courier new]/mnt/btrfs[/FONT] on my machine.
There is a symlink at [FONT=courier new]/btrfs[/FONT].

There are a number of subvols within this,

[FONT=courier new]/archive
/backups
/games
/home
/music
/photos
/temp
/videos
/virtualmachines[/FONT]

[FONT=courier new]/home[/FONT] is mounted at [FONT=courier new]/mnt/btrfs/home/[/FONT]

When I delete an item from any folder in 'home' the items goes to the Recycle Bin correctly.  I can recover and empty easily.

When I delete an item from any other subvol the object(s) go to [FONT=courier new].Trash-1000[/FONT] within that subvol and this does not appear in my bin but has to be removed manually.

I suspect this is a permissions problem but cannot see what that could be.

Can anyone help with some suggestions for me?

---

### Post by bab1 on 2014-10-15
> **sir-marky said:**
> I have a three 3TB discs in a BTRFS RAID 1 configuration mounted at [FONT=courier new]/mnt/btrfs[/FONT] on my machine.
There is a symlink at [FONT=courier new]/btrfs[/FONT].

There are a number of subvols within this,

[FONT=courier new]/archive
/backups
/games
/home
/music
/photos
/temp
/videos
/virtualmachines[/FONT]

[FONT=courier new]/home[/FONT] is mounted at [FONT=courier new]/mnt/btrfs/home/[/FONT]

When I delete an item from any folder in 'home' the items goes to the Recycle Bin correctly.  I can recover and empty easily.

When I delete an item from any other subvol the object(s) go to [FONT=courier new].Trash-1000[/FONT] within that subvol and this does not appear in my bin but has to be removed manually.

I suspect this is a permissions problem but cannot see what that could be.

Can anyone help with some suggestions for me?
This is ***not*** a permissions issue.  This is *expected* behavior.  Only items deleted from your /home directory or its sub-directories show up in your *"Recycle Bin"* (really the /home/$USER/.local/share/Trash).  

In addition all items in a separate partition show up in /<the-root-of-the- partition>/.Trash-$USER-UID.  This is also not something you can overcome with sym-links.  Each partition has its own location schema (inodes).  The OS understands which partition the file or directory is located. 

If you were to add a file at /srv or /opt or any other directory outside of your home directory and then delete it,  the file would just be deleted.  It's only because the items you are trying to delete are on a separate partition that you see them move to the a trash directory at all.

---

### Post by sir-marky on 2014-10-15
That's not fun at all.

I guess the only solution there is to create a bash script to delete the .TRASH-1000 folder from the subvols upon system start/shutdown/whenever to clear them out but, of course, that wouldn't allow me to recover files from them easily.

A 'super bin' option would be better to collect to content of all the TRASH-1000 folders including the regular bin.  I don't know if such an app exists.

---

### Post by rbmorse on 2014-10-15
If you mounted your array at:

/media/btrfs 

rather than /mnt/btrfs you would get the desired behavior from the trash bin, but it might change other aspects of they way your system works.

---

### Post by sir-marky on 2014-10-17
Could I get away with symlinks, hard or soft to do the same result?
The reason I have the array mounted at [FONT=courier new]/mnt[/FONT] rather than [FONT=courier new]/media[/FONT] is to separate it from my user.

---

