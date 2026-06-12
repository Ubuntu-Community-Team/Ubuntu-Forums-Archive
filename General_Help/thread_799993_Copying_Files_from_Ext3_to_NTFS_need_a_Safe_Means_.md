---
title: "Copying Files from Ext3 to NTFS need a Safe Means of doing it"
date: 2008-05-19
forum: General Help
---

### Post by linuxology on 2008-05-19
Scenario:  Two 250 GB drives. One drive holds Windows the Other holds Ubuntu.  I can copy files from NTFS into EXT3 file system natively in Ubuntu.  The problem is a can not go the other way.  Can a boot disk like Hiren's boot disk copy files safely for me?  I have read that EXT3g is buggy that allows you to write to ntfs from within Ubuntu.  This method of copying within Ubuntu to NTFS does not sound very safe, so I am looking for a safer way of doing it.  Any suggestions?  Thx.

---

### Post by unutbu on 2008-05-19
Have you tried mounting your ntfs partition using the ntfs-3g driver? According to [this wikipedia page]("http://en.wikipedia.org/wiki/NTFS#Linux"), it is safe for reading and writing to NTFS.

This may not be a big deal for you... but just in case: ext3 has the ability to create symbolic links between actual files and, um, phantom files (my terminology). I don't think NTFS has an equivalent concept. So strictly speaking, making an exact copy from ext3 to NTFS is impossible.

---

