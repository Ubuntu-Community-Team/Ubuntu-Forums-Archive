---
title: "file sync between ubuntu and xp"
date: 2008-05-10
forum: General Help
---

### Post by karq on 2008-05-10
Hey everyone

How can I sync my files between ubuntu and xp? Ubuntu is on my laptop and xp is on my pc, so I have to sync them over home network.

---

### Post by hyper_ch on 2008-05-10
what kind of files? you might consider using a common partition

---

### Post by gasolino_ on 2008-05-10
I use "unison" (or "unison-gtk", with the GUI). Unfortunately it doesn't support sync over SMB, so you have to mount the shared folder with smbfs or cifs ([here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=(cifs)") or [here]("https://wiki.ubuntu.com/ComprehensiveSambaGuide?highlight=(samba)")).
Then you can sync as with local folders. rsync is very good, also. No SMB protocol anyway.
On the win side SyncBack works very well for me. This way you have to share folders from Ubuntu before syncing, obviously. If you don't know how read the links.

---

### Post by tacutu on 2008-05-10
+1 for unison.
you don't really need a shared folder, you can sync via ssh if you want, but in that case you need unison installed on both machines (so it's almost like a server-client setup)

---

### Post by karq on 2008-05-10
I want to sync my pictures, so that I have a backup of them on the pc.

---

### Post by TVC15 on 2009-03-21
Hi there,

Backup utilities seem to be a hot item on the forum.  A lot of people want something that looks and feels similar to the popular Windows tool Syncback.

For Linux, the best backup tool for me (and surely many others) is rsync.
Best of all: rsync now has a GUI called grsync that you can find in the Ubuntu repositories.
Looks and feels a lot like Syncback and also works on Samba shares or mounted network drives or over an ssh, ....

Very much worth giving a try!


Good luck!

---

