---
title: "Restricting access to mounted volumes"
date: 2008-04-07
forum: General Help
---

### Post by habrys on 2008-04-07
I'd like my hardy to mount the volumes from /etc/fstab only for one user and for others not. How can I achieve it? The goal is to have all the volumes visible on desktop only when logged in with the chosen user. For all others there should be no disk icons on the desktop visible.

I have following file systems auto-mounted via fstab:
ext3
ntfs
vfat
smb
nfs

I can achieve it only partially using umask (only for vfat and ntfs and the disk icons are still there, but there is no access to volume after clicking it).

I solved it on feisty:
[http://ubuntuforums.org/showthread.php?t=599358]("http://ubuntuforums.org/showthread.php?t=599358")
but the solution doesn't seem to work on hardy any more.

---

### Post by habrys on 2008-04-08
nobody?

---

### Post by Peter09 on 2008-04-08
Not sure about this, but if you go to Places->Connect to Server I think it mounts it to your desktop. It is a permanent mount point I think .... never really used it in anger so not to sure though.

PC

---

### Post by habrys on 2008-04-08
I'll try this out, but I think it was not permanent last time I used "Connect to Server" dialog. Besides it's only good for servers, like samba, nfs, ftp etc., right? I cannot mount local filesystems, like vfat, ntfs ext3 with this dialog?

---

### Post by Peter09 on 2008-04-08
I think it is permanent, but you are correct in saying that it will not mount local file systems.

PC

---

### Post by sdennie on 2008-04-10
One thing you could try would be to create a .hidden file in each users ~/Desktop directory.  A .hidden file for nautilus just contains the names of folders that shouldn't be displayed when hidden folders aren't shown.  I don't have any desktop icons because I turned them off long ago and can't remember how but, I imagine that the icons are displayed via nautilus so, it might work for you.

---

