---
title: "Cannot copy files with certain characters to a samba share"
date: 2008-03-04
forum: General Help
---

### Post by speedsix on 2008-03-04
My fstab entry looks like;

//desktop/myth  /mnt/myth  smbfs  credentials=/root/.smbcredentials,dmask=0777,fmask=777  0  0


When I try and copy files over to this share that have things like ?'s in the filename, they won't copy with a 'no such file' message. I'm actually trying to use rsync but even a manual copy doesn't work.

Any ideas?

---

### Post by ajgreeny on 2008-03-04
Rsync and grsync won't copy files with names containing certain characters, as I know from the experience of doing backups to a USB external drive .  Many of the ripped tracks from CDs will not backup because the ripping software gives them names with commas, exclamation marks and all manner of other things from the CD track names.  I ended up manually changing the names to make sure they were all backed up OK.  I also always get a number of files that won't backup every time I use grsync, but they are only the files in /home/username/.nautilus/metafiles folder, all of which have a colon (:) and at least one percent character (%) in the file name.  Whether this is done to avoid backing up files that are not really worth the effort, or it is just something to do with file naming protocol, I don't know.

---

