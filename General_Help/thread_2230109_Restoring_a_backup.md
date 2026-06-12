---
title: "Restoring a backup"
date: 2014-06-17
forum: General Help
---

### Post by kahootbot on 2014-06-17
A few years back I went through this tutorial: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I have a backup of my hard drive which has since went out. I'm wondering how to restore the files from there (preferably without reparitioning my hard drive and just mounting/extracting the files)

Archive Manager strangely just seems to extract the same bz2 file when I extract it so no luck there.
Any suggestions?

---

### Post by TheFu on 2014-06-18
So, did you use **tar**?  Tar isn't imaging, so you'll need to install a fresh OS of the same release onto the new HDD first, then restore the files from the backup running it from the same location where the backup was created.

```
sudo -s
cd /full/path/to/where/you/want/things/restored/
tar zxvf /full/path/to/tar/file.tar 

```
Does that make sense?

---

